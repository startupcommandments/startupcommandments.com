---
layout: post
title:  "CTO Commandments"
date:   2017-04-08 11:37:30 +0200
permalink: /cto-commandments
---
## **Frontend**

### Never use server side rendering
Server side rendering simply causes you to be lazy. Server side logic leaks into your frontend, making caching a bitch, plus requires you to rebuild data access for native apps anyway. Frontend is hosted as a static site and communicates via documented APIs only.

### Host your web app frontend (and websites and any static content) on static hosting
Using a service like S3 to handle all your static needs takes a huge stress off your plate.

### web frontend should be responsive be default and work with touch screens
Zero excuses for not being response with at least one breakpoint for tables/mobile. Also, test any UI components you want to use for touch interactivity. That can be very annoying if something doesn't allow for taps, etc.

### Use a frontend framework that allows for modular development
Frontend tech evolves very fast. So build your frontend in a modular way so that migration to better frameworks in the future is relative smooth.

---

## **Backend**

### Only store unique data in the database
What this means, is only store information that changes for different users/accounts. Do not store data that is the same for all users. Just stick that global data in a JSON file.

### Use the right database for the job
Relational data belongs in a relational database. Non-relational data belongs in a non-relational database. Got it?

### Premature optimization is **the** root of all evil
Build on a solid foundation (using the rules listed here), but do not stress much if some of the walls are a little shaky. Just note it in your bug/task tracking software and revisit when you have time. Tech debt **will** happen, but the closer to the foundation, the more painful it will be to fix.

### Use a tried and true API framework for the language you are the most comfortable with
For NodeJS, use Hapijs or Express. Ruby use Rails obviously. Python use Flask. Elixir use Phoenix. PHP, not even once.
Frameworks help you bootstrap quickly and provide enough opinions on how to do things so everyone on your team can reference the same documentation and get similar results.

---

## **Operations**

### Use other peoples tech **except** for your differentiator
Using 3rd party services to get your product out the door is great! But do not depend on a 3rd party for the aspect of your product that is unique.

### Deploy to production several times a day
If it takes a week to deploy to production you are doing it wrong. Every change should trigger a build server with tests deployment. At the very least, a local deployment script should handle all builds and push to remote servers. The faster you can deploy to production the faster you can fix issues in production.

### Never SSH into the servers
This is a terrible practice, and will make your application non-deterministic. If you cannot deploy your application to a brand new server automatically without using SSH to config something on the server, you will be in a lot of pain when that server dies a fiery death.

### Agree on tabs vs spaces
This is a no brainer. Obviously tabs that expand to spaces in your text editor.

### Never commit secrets even in a private repo
There is no guarantee the repo will stay private forever. And this gets you in the habit of using variable files. Don't forget to add the variable file into .gitignore!

### The cloud is a life saver but use it correctly
In general, use VPS. Do not use proprietary app servers (such as app engine). Use one of the 3 providers (AWS, Google, Azure). As mentioned else where, do not SSH into these servers. Only deploy your code via scripts. Use HTTPS on every server and make it default. Use load balancers over multiple small servers vs one large server. Cloud servers can and will die.
