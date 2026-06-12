---
title: "No &quot;quiet splash&quot; but still no boot messages"
date: 2018-08-22
forum: Installation &amp; Upgrades
---

### Post by nocom2 on 2018-08-22
I have a multi boot/EFI system. I started with Windows 10, installed mint 18, later Ubuntu 18. So I had Windows 10, Mint 18 and Ubuntu 18 in that order using the last one as default system. I removed &#8220;quiet splash&#8221; from GRUB_CMDLINE_LINUX_DEFAULT="" and could see the boot messages.  
 
 To test some options I next installed Ubuntu 16 over Mint 18. Ubuntu 16 installed a graphic grub with no boot messages. Without cheking I assumed that the &#8220;quiet splash&#8221; is default for any ubuntu system. I left that as it was because I only wanted to test some options. After the test I used grub-install from ubuntu 18 and deleted the partition with ubuntu 16. 

I have not been able to get the boot messages back. There is some kind of gray/brown color when I boot, in the same color as the graphics boot screen I got from ubuntu 16. There is no &#8220;quiet splash&#8221; in */*etc*/*default/grub, nor can I see one when I edit the commandline during boot. There are a lot of suggestions on the web, but none worked. The current /etc/default/grub is listed below. It appears as if there is some persistent left-over from ubuntu 16. Could the be? If so, how can I test that?
 
 Anybody any idea about what is wrong with my grub setup?
 
 ```
GRUB_DEFAULT="0"
 GRUB_HIDDEN_TIMEOUT="0" # had it commented out as well, no difference
 #GRUB_HIDDEN_TIMEOUT_QUIET="true"
 GRUB_TIMEOUT_STYLE="hidden"
 GRUB_TIMEOUT="10"
 GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
 GRUB_CMDLINE_LINUX_DEFAULT=""
 GRUB_CMDLINE_LINUX=""
 
 
 # Uncomment to disable graphical terminal (grub-pc only)
 # When uncommented the screen turns full black, like a console indeed
 GRUB_TERMINAL="console"
 
 
 # The resolution used on graphical terminal
 # note that you can use only modes which your graphic card supports via VBE
 # you can see them in real GRUB with the command `vbeinfo'
 #GRUB_GFXMODE="640x480"
 
 
 # The option below was suggested in one post, it made no difference
 GRUB_GFXMODE="text"
```

---

### Post by T.J. on 2018-08-25
Try adding "nomodeset" to your boot parameters.  It is likely that your video adapter is hiding the messages.  Adding "nomodeset" will prevent it from changing modes before it arrives at the point where it actually switches to X11.

---

### Post by nocom2 on 2018-09-03
Thanks T.J. I guess you meant something like `GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"`? It did not work alas. Everyting remained exactly as before. Do you think I should reinstall Ubuntu?

`.

---

