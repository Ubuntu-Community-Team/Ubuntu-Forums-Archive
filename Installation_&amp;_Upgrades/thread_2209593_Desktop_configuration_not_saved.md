---
title: "Desktop configuration not saved"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by emarrodz7 on 2014-03-06
Hi everyone!

I just managed to install Ubuntu along with Win7, thanks to the help of all of you. Everything was working fine but I wanted to adjust the way GRUB behaves and default to Win7, as my partner is the one who use it more for some games. I used GRUB Manager and tried several changes but, in the end, it resulted pretty much complex than expected. I reduced to 2 simple options, Win 7 and Ubuntu but, since then, my entire Desktop configuration got lost and every time I try to reconfigure the desktop it gets lost again when restarting. Not just that but I try to change certain configurations, as wireless connections, I receive an error message as me not having the proper privileges.

I really would like some insight on how to recover the ability to save my desktop configurations, my privileges and, if possible, how to edit GRUB without messing everything else again!

Thanks in advance!

---

### Post by grahammechanical on 2014-03-06
I am not sure what Grub Manager you are using. But if it is the one I think that it is, then it has a save to MBR option in one of its menus. You are changing the configuration files but you need to re-install Grub into the MBR for the changes to take effect.

I do not advise removing the Recovery mode option from the Grub menu.

How are you trying to change those wireless configurations? By editing the configuration scripts? You cannot do that as standard user. And that is to protect us from ourselves. Why not use the system utilities that come with Ubuntu. You will then be asked to Authenticate and when you enter your password it will be enough.

You need to read this

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Regards.

---

### Post by emarrodz7 on 2014-03-06
I'm afraid I may have been misunderstood. The actual problem with the GRUB is secondary. The main problem is that now, when I start session the desktop is configured as default, as first time boot. Then I go and set up everything to my liking but then, when restarting everything is back to default. About the wireless connections I'm editing them as usual, using the GUI. Originally I was able to do it, I entered my own DNS and everything worked fine, is just after I messed up with the GRUB that this happens. I don't see the possible relation but that's the only change I've made.

Now for GRUB, if you recommend a better manager I'll be happy to try it. I really don't want to use MBR because I'm afraid Win 7 won't be able to boot up again and I'll have to reinstall it once more.

Thanks in advance!

---

### Post by ajgreeny on 2014-03-06
Can you run the following commands one by one in terminal and replace the word *user* in the second with whatever you use as username ```
ls -la /home
ls -la /home/*user*
```
They may give us a clue to a reason for the loss of all your configuration when you reboot.

---

### Post by emarrodz7 on 2014-03-12
I'm very ashamed as I found out what the problem was. Somehow the session initiated was for the guest account. I have no idea why this happened but now is working fine. I reviewed ths several options at the GRUB menu to see if I messed it more than I wanted but I couldn't find the error. Now is everything fine and I really appreciate all your help as always!

---

