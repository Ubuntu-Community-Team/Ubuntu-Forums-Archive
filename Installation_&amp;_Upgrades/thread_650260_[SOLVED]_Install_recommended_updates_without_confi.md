---
title: "[SOLVED] Install recommended updates without confirmation"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by IanB2 on 2007-12-26
I have an elderly relative that I'd like to switch to Ubuntu. In other words I want to set up a system that 'just works' with no intervention needed by my relative.

I'd like to be able to set up the system such that not only 'install security updates without confirmation' is enabled (GUI - software sources - updates) but I'd like to include 'recommended updates' as well.

Is there a configuration file that I can adapt to achieve this?

---

### Post by Partyboi2 on 2007-12-26
Maybe this is what you are looking for:
Go to Software Sources. (System>Admin>Software Sources)
On the 3rd tab (Updates) select "download all updates in the background" or "install security updates without confirmation"

---

### Post by IanB2 on 2007-12-26
Thanks but I've already got this set in software sources and whatever I choose the update manager still appears (when there are new updates) on the task bar.

I'm trying to ensure that ALL software updates install WITHOUT any need to enter passwords etc as this will only confuse my relative. (Her Windows PC is currently set to install updates without any need for any form of intervention ..... is this possible in Ubuntu?)

Thanks.

---

### Post by Partyboi2 on 2007-12-26
I think cron will do the job or atleast get you going in the right direction., though I haven't really played around with it yet.
[http://kevin.vanzonneveld.net/techblog/article/schedule_automatic_updates_on_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/schedule_automatic_updates_on_ubuntu/)
[http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/)
[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

---

### Post by Casual Fan on 2007-12-26
I'm not certain, but this would make a great distro for the elderly. Seriously--large fonts, automatic updates. Someone should do this. Just not me.:)

---

### Post by IanB2 on 2007-12-27
> **Partyboi2 said:**
> I think cron will do the job or atleast get you going in the right direction., though I haven't really played around with it yet.
[http://kevin.vanzonneveld.net/techblog/article/schedule_automatic_updates_on_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/schedule_automatic_updates_on_ubuntu/)
[http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/)
[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

Excellent and thanks!

I used [https://help.ubuntu.com/community/Au...ecurityUpdates](https://help.ubuntu.com/community/Au...ecurityUpdates) which is working nicely.

---

### Post by runesvend on 2008-01-21
The guide that the poster linked to above ([https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)) requires one to be logged in as root, right? I get an error message when executing the *aptitude update* command which is because it doesn't have sudo rights. So there are two options:

[LIST]
[*]One could put in a *sudo* before the commands but that would prompt for a password, which kind of defeats the purpose of being automatic

[*]Log in as root
[/LIST]

None of these options are really viable are they? Or am I missing something?

---

