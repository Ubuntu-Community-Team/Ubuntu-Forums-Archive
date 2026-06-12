---
title: "UNIX // GNU/Linux"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by johnalphen on 2010-04-17
Hi friends! any expert on Linux Ubuntu. 
1. I have windows xp on my notebook compaq presario v2000. 
2. Wanted to load linux as dual boot. 
3. Tried with Suse linux, but there was some blank or black screen problem after installation. 
4. Someone suggested Ubuntu linux. 
5. Downloaded and burned ubuntu on a cd. 
6. But this time during installation during partitioning there was a serious problem. 
7. On ubuntu webpage they say for partiioning i will get 4 option, but i got only three options in my cd. 
8. The missing option was the most important , which was required for dual boot. " Guided resize and use free space". 
9. So i had to abort my Ubuntu installation as using any other option could have effected my current xp installation or might have formated my whole notebook. 
10. So any comment why the dual boot partitioning option was absent in my ubuntu cd. 
11. Or there is some thing to be activated in my notebook setting to enable dual boot. 
12. Waiting for your expert comments. 
13. Thanks!!!

---

### Post by HermanAB on 2010-04-17
Howdy,

The Ubuntu installer is still kinda clunky.

If you want an automated installer that will handle Windows without tears then you got to use Suse, Mandriva or Fedora.  With Ubuntu, you got to change the partitioning manually before installing.

---

### Post by Iowan on 2010-04-17
Moved to Installation & Upgrade

---

### Post by presence1960 on 2010-04-17
> **johnalphen said:**
> Hi friends! any expert on Linux Ubuntu. 
1. I have windows xp on my notebook compaq presario v2000. 
2. Wanted to load linux as dual boot. 
3. Tried with Suse linux, but there was some blank or black screen problem after installation. 
4. Someone suggested Ubuntu linux. 
5. Downloaded and burned ubuntu on a cd. 
6. But this time during installation during partitioning there was a serious problem. 
7. On ubuntu webpage they say for partiioning i will get 4 option, but i got only three options in my cd. 
8. The missing option was the most important , which was required for dual boot. " Guided resize and use free space". 
9. So i had to abort my Ubuntu installation as using any other option could have effected my current xp installation or might have formated my whole notebook. 
10. So any comment why the dual boot partitioning option was absent in my ubuntu cd. 
11. Or there is some thing to be activated in my notebook setting to enable dual boot. 
12. Waiting for your expert comments. 
13. Thanks!!!

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

