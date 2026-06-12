---
title: "Hibernate/Suspend not working when lid closed."
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by Dr. Feltersnatch on 2006-12-23
Greetings,

I had upgraded to edgy from dapper a while back, but encountered an issue with afterwards.  Hibernate and suspend both work when initiated from the power icon or the shutdown button. However, the way I used it with dapper was I would close the laptop lid and Ubuntu would go into hibernate. After the update, this no longer occurs. What will occur is the system will appear to go into hibernation, but Gnome will just close and go back to the login screen prompting for user name then password.  No applications I had open in a Gnome session are still open after I log in. 

 /var/log/messages shows:
Dec 23 14:36:37 localhost gnome-power-manager: (jorg) Hibernating computer because the lid has been closed on ac power

So far I have run through this thread:
[http://ubuntuforums.org/showthread.php?t=287524&highlight=hibernate+edgy](http://ubuntuforums.org/showthread.php?t=287524&highlight=hibernate+edgy)

I also installed the hibernate script.

Any ideas?

Edit: 
Could a mod move this to the laptop section?

---

### Post by findik1 on 2006-12-30
I have similar problem, I am a new user (ver 6.10) so I dont know whether it can solve your pronlem at least you can try my experience and it may work for you: from applications>system tools>Config edit
click apps then open gnome-power-manager
then change the setting to: action_ac_button_lid  suspend
                                        action_battery_button_lid suspend
then it did work for me.

you can also use preferences>power management tool to arrange setting with a mouse.

Here I want to tell a problem that I had:
after I made an update this configuration got lost and system set to initial config so suspend with lid did not work anymore, then I had to reconfig the things.
Another problem arised after I used some program a week later (maybe not related at all, not a specific prog,) when I closed the lid sleep/suspend mode, LCD becomes blank, and start by flashing the led (so far everything is OK!) but cannot go to SUSPEND mode at all (normally after flashing 5 times laptop was starting sleeping). when you open the lid nothing changes, LCD blank, so bigger problem, you have to reboot the laptop to startover. Any SUGGESTIONS what to do? 

Happy new year to all!
FINDIK

---

