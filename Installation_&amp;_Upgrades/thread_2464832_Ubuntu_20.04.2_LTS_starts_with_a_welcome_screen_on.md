---
title: "Ubuntu 20.04.2 LTS starts with a welcome screen on every restart"
date: 2021-07-13
forum: Installation &amp; Upgrades
---

### Post by bikertales on 2021-07-13
Hi, 

For some reason on every restart Ubuntu 20.04.2 LTS displays a  welcome screen and i need to create a new user on every restart.  Existing user are not displayed. I was using 20.04 and I simply restarted the laptop after completing  my work. No update was installed by me I think there could have been an  background 20.04.02 update. Post the issue, updated ubuntu with patches  hoping it will fix the issue, but the result is the same. 

There was something strange in the last session i could not do basic   mv with sudo to /usr/local/bin and after few attempts i could, may an update was going on. This  never happened before.  Was following [https://book.kubebuilder.io/quick-start.html](https://book.kubebuilder.io/quick-start.html) and installing kubebuilder. sudo did act funny. 


 Data related to the existing users is present.


 How do i use my existing logins? SOS request please help.

Thanks
Prashant

---

### Post by TheFu on 2021-07-13
This is not a standard Ubuntu install.  If using Kubernetes, wouldn't that be recreating the "container" on each boot?  Wouldn't that remove the core OS stuff on each rebuild?  I'm just asking questions. I've never used K8.

The power of Linux containers comes from them NOT allowing local data to be retained.  They are all about "compute" and accessing DBs on different systems. Yes?  If you want the same user to be available between fresh container builds, then add the users do the container build process.

Or I could be completely wrong.

---

### Post by bikertales on 2021-07-13
This is a standard Ubuntu installation. Just wanted to lets every one know that sudo acted strange during the work i was doing.

---

### Post by TheFu on 2021-07-13
> **bikertales said:**
> This is a standard Ubuntu installation. Just wanted to lets every one know that sudo acted strange during the work i was doing.

I've not seen anything funny related to sudo on any of my 20.04 systems.  The only "funny" things I've seen are related to broken snaps, broken systemd stuff, and complex netplan setups.  Everything else in 20.04 server has been working as expected.

So, if you'd like help, show us exactly how to reproduce the problem in 1 or 2 commands. Show the exact command and show the exact output and show why this isn't the expected result.

Please.

---

### Post by bikertales on 2021-07-13
ok it must be my oversight and i am wrong about sudo. Would you know how to fix the welcome screen issue.

---

### Post by TheFu on 2021-07-13
My servers and K8 containers don't have GUIs. Sorry.  

If I access via a console, then only a "Login: " prompt is displayed.
[ATTACH=CONFIG]288817[/ATTACH]
See attached.  Sorry about the image. My console access doesn't support text select/paste.

If running a GUI, then the answer will be dependent on the release and DE and which display manager is being used. 
My GUIs are all configured to require someone to type in a username for security reasons.  We never want a list of valid usernames to be listed in our environment.  That's just our security policy.

In general, any userids higher than 1000 should show in the list. At least that's my understanding.  Google has a number of suggestions, but they all appear to be related to either userids under 1000 or for people with autologin.

---

