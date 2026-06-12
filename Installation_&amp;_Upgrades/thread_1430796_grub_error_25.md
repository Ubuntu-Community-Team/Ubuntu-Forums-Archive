---
title: "grub error 25"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by ferdyfer on 2010-03-15
Hi,
 
I've been using Ubuntu 8.10 (I think) for a little under 2 years and haven't had any problems. Just before the weekend, I installed some updates and used the blue arrows in a circle to reboot the machine. Now it stalls on grub error 25. I have searched for some information on what to do but most of it seems to talk about what to do if you have partitioned your computer. Ubuntu is the only OS on my computer. What do I need to do to fix this problem if I don't have Windows on my computer? Unfortunatley, if I need the installation CD, I will need to make another one. I gave it away to someone to install it on their computer. Is there a way I can make another one now that it's 2 versions away from the newest? (If I need it of course...)
 
Thanks.

---

### Post by benrboone on 2010-03-15
You can still download the live cd from here: [http://ubuntu.cs.utah.edu/releases/8.10/](http://ubuntu.cs.utah.edu/releases/8.10/)
once you get the live cd you can reinstall grub using this  post 
[http://ubuntuforums.org/showthread.php?t=1113903](http://ubuntuforums.org/showthread.php?t=1113903)
hope that helps.:)

---

### Post by presence1960 on 2010-03-15
> **ferdyfer said:**
> Hi,
 
I've been using Ubuntu 8.10 (I think) for a little under 2 years and haven't had any problems. Just before the weekend, I installed some updates and used the blue arrows in a circle to reboot the machine. Now it stalls on grub error 25. I have searched for some information on what to do but most of it seems to talk about what to do if you have partitioned your computer. Ubuntu is the only OS on my computer. What do I need to do to fix this problem if I don't have Windows on my computer? Unfortunatley, if I need the installation CD, I will need to make another one. I gave it away to someone to install it on their computer. Is there a way I can make another one now that it's 2 versions away from the newest? (If I need it of course...)
 
Thanks.

See [here]("http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors") for GRUB error25 for Legacy GRUB. You are going to need the Live CD for your version of Ubuntu. Once you get it do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

This will show us a lot about your setup & boot process. Currently all we can do is guess.

---

### Post by ferdyfer on 2010-03-19
ok so now I'm really in a pickle! I tried booting my computer from the CD and I ran the program without any changes. However, it won't even get to the desktop and I can't reboot nor shut down my computer now. 
 
The final line of text that is currently on the screen is:
 
[ 0.512037 ] Kernel panic - not syncing: attempted to kill init!
 
What does this mean and what do I need to do now?? I can't even turn the computer off!!! Should I just unplug the thing and see what happens?
 
thanks

---

