---
title: "Allow non-admin user to auto-update?"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by asktoby on 2007-05-13
I have built a Ubuntu 7.07 box and plan to give it to my sister.
I don't intend to give her admin permissions for her own protection: she's not a strong computer user.
I would like the box to automatically find and install updates.
How can this best be done please?

---

### Post by seshomaru samma on 2007-05-13
i am not sure but you can define sudo rights and limit them to specific actions in /etc/sudoers
for example
```
sesho ALL = NOPASSWD:  /sbin/reboot
```
means user sessho can only go sudo reboot and any other sudo command will be rejected
however i don't know if you will be able to define installing updates

another option is for you to ssh to her machine and update it yourself

---

### Post by u.li on 2007-05-13
If you want the system to automatically update itself, you can set up cronjobs (or anacron) to do aptitude update and aptitude upgrade in regular intervals (like once a week).

Look here: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

But it's probably better if you do it yourself via SSH or whatever

---

### Post by asktoby on 2007-05-13
I think the machine will be turned off most of the time.
Will going the anacron route mean that, if an update is missed because the machine is turned off, the update-check will occur at boot time the next time it's turned on?

---

### Post by asktoby on 2007-05-20
To answer my own question, yes it does: That's anacron's raison d'etre!

Is there any way I can manually trigger anacron? At the moment, I've put an apt-get update install script in /etc/cron.daily but every time I tweak it I have to wait 24 hours for it to get triggered so I can test it! Time consuming!

---

### Post by asktoby on 2007-05-20
Ton answer my own question again:
# anacron -f -n
will force anacron to run all its jobs immediately.
Any errors are sent to the mail user defined in root's crontab by the line
MAILTO=username
For the user 'username' to collect that error message, you will need a mail reader such as mutt, and you will need to install the linux app "mail" by going
# apt-get install mail
You may also need sendmail... I'm not sure.

---

### Post by Rashid584 on 2007-05-20
Thansk for that info...may come in useful ;)

-Rashid

---

