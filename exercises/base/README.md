# Apple Support Exercise 1 - Base

Completion Time frame: `24 hours`\
Actual Required Time: `1 hour`\
_(I tested and completed this in just under 40 minutes)_

Allowed Packages: `discord.js@14.7.1`\
Included Files: `config.json`

> Do not use Typescript! Contrary to AppleSupport being build and ran with compiled typescript.

---

In this exercise you will create a functional bot with a basic ticketing system.\

> Based on the current Apple Support bot structure.

Follow the instructions below for a detailed explanation.

**Follow the standards located on dev branch home.**

### Do's and Dont's

|   **ITEM**    | **ALLOWED** | **INFORMATION**                                                                                                                                                                                                                                                                                                                                            |
| :-----------: | :---------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **CodePilot** |     ❌      | _While CodePilot is an amazing tool I use daily, for this exercise please do not use it. I want to know you have the ability to program without it assisting you. You can always use google to help find a solution to a issue you are having. If you cannot explain how something was made I will instantly have a problem with trusting your integrity._ |
|  **Google**   |     ✅      | _Google is always allowed. No one has perfect memory and Google is a great tool to quickly find a solution to solve a issue you may be having._                                                                                                                                                                                                            |
| **Bot Base**  |     ❌      | _You should not download or use a discord bot base. I want you to create this bot from nothing. For this exercise it is okay to include everything in `index.js`_                                                                                                                                                                                          |

# 🏗️ Structure

### **📜 Tickets Forums Channel**

`⚠️ Community Server Required*`

Apple Support utilizes discord new Forums channel type\

> Introduced in [v14](https://discordjs.guide/additional-info/changes-in-v14.html#forumchannel)

If this channel does **not exist** the bot should be able to determine this and regenerate the channel on demand.

### **📝 Ticket Threads**

Each ticket is a separate [thread](https://discordjs.guide/popular-topics/threads.html#thread-related-gateway-events).\

> Introduced in [v13](https://discordjs.guide/additional-info/changes-in-v13.html#threads)

Tags are not important for the exercise.

When a ticket is created it will be assigned a ticket ID.\

> For this exercise you can SKIP ID assignment.

Finally, the opening thread "message" should include a embed with the users name, profile photo, and the content of the message they sent when opening it.
<img src="https://user-images.githubusercontent.com/63246000/211909409-4c04e2b0-186f-4b0f-a98a-300100e77fa4.png" width=25% height=25%>

### **📢 On DM Received**

This event is triggered whenever someone sends a direct message to the bot\
When the message is delivered the bot should determine the next course of action.\

> If ticket exists, post in ticket.
> If ticket does not exist, create ticket thread **and** then post.

Message format in the thread can be sent by the bot like so... `'User#0000: message content'`.

💡 Additionally, include the filter we setup during the initial voice call interview. Make sure users are unable to send mass ping tags.\

> The filter should use the configured array including in the base located in `config.json`

### **📨 On Staff Respond**

When a staff responds to the ticket it should send a DM to the user.\

> Staff is defined by anyone in the support guild who can see the thread.

Rules:\

- Never expose a staff members name.
- If message has a prefix of `.` it will not send to the user.

# 🧠 Problem Solving Skills

How are you going to store a ticket and how will you determine if the user has a open ticket already?\

> Do not database **anything**, should continue working after restart (no caching).
