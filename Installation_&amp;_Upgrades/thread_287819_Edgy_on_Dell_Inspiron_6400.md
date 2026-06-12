---
title: "Edgy on Dell Inspiron 6400"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by awarberg on 2006-10-29
I've installed Ubuntu 6.10 on my Inspiron 6400 laptop, bios rev. A09. The (clean) installation went flawlessly.

But there are some things that seems odd to me:

1) Edit: I wrote that Ubuntu didn't detect my dual core cpu. That was an error, the generic kernel uses both cores, sorry.

2) The screen resolution was set to 1024x768. The native resolution of my screen is 1280x800. By installing a patch that modifies the bios of my Intel GMA 950 graphics card I can use the native resolution. While this is a bit scary I chose to believe it is necessary because intel misconfigured the bios of the video adapter (though I still wonder why XP doesn't complain about this...).

The worst problem is that I am no longer to adjust the brightness of my screen by pressing FN and the up or down-arrow. Maybe this is due to the video bios modification.

3) The standby function doesn't seem to work correctly. When I press FN standby Ubuntu starts going to standby. The monitor is switched off and the harddisk activity indicator lights up now and then. But the system never goes into standby.

What is worse, when I want to take it out of standby and press the power button as I'm used to nothing happens. In fact I can press all the keys I want, Ubuntu stays down. I need to hold the power button for 10 seconds - or remove the battery - in order to  use the system again. 

Standby on Windows XP works superbly. It takes a few seconds to put the computer into standby as well as to take it out again.

4) Switching between users requires me to type in the same password twice.

Example: I have two users logged in. In my active session I press the shut down symbol and select Switch User. This brings me to login screen. Here I type the username and password for the other - logged in - user. The system asks if I want a new session or to just resume the active one. I choose the latter. But now Ubuntu wants me to type the password again! I just typed it 3 seconds ago so I am clueless why it is necessary to type it again.


In summary I am impressed with the installation routine. The visual details are great too. I like that you simplified the status indicators for the startup and shutdown sequences (I really didn't need to know which services had been started).

But some of the issues I have mentioned greatly affects my daily work. It takes too much time to compensate for them. 

So now you know about some issues for Ubuntu 6.10 on the Inspiron 6400. I believe this laptop is very mainstream so many people have it. At least I see it on campus quite often. I hope you will look into the problems.

Best regards
Andreas

Edit: I forgot to add that Ubuntu is missing a built-in tool for discovering wireless networks. I know that gnome-network-manager will help a lot but it is not installed per default.

---

