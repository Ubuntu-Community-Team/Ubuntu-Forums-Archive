---
title: "can't install ubuntu 10.10 because of nvidia"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by anyone2009 on 2010-10-10
Hi ,, today I try to install ubuntu 10.10 final release but it's stop and hangs after the progress bar completed and the screen appear strange colors overlapping ,, I have nvidia graphic card and I don't have internal graphic card so I can't install it ,, 
I think that may be the problem from the cd so I test it on my laptop and every thing works fine ,, so please help me to install it on my desktop :(

---

### Post by sveterv on 2010-10-10
If you are before installation, and you boot from a CD, you see menu, choose language you want and hit F6 key, after this you will see little menu extended at the right bottom of the screen, pick "nomodeset" from it (you will see "x") and then hit ESC key and ENTER, now your installation should be possible, I hope.

---

### Post by anyone2009 on 2010-10-10
> **sveterv said:**
> If you are before installation, and you boot from a CD, you see menu, choose language you want and hit F6 key, after this you will see little menu extended at the right bottom of the screen, pick "nomodeset" from it (you will see "x") and then hit ESC key and ENTER, now your installation should be possible, I hope.

You are the man 

really thanks 

thaaaaaaaaaaaaaanks ^_^

---

### Post by sveterv on 2010-10-10
No problem :)

---

### Post by Silvertones on 2010-10-10
I had to do this:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.

---

### Post by anyone2009 on 2010-10-10
> **Silvertones said:**
> You also need to edit the grub.cfg file so it'll work each time.
You need to add the word "nomodeset" after quiet splash.
Like this:
linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=4c1fffed-2781-4bbc-a034-4e14ead82f02 ro   quiet splash nomodeset
grub.cfg is in filesystem/boot/grub
you'll need to sudo in terminal to do this.

thank you very much ,, really 
after I install it and boot to it I face the problem again ,, then I do what you tell me to do and it's works ,, and now I download the driver of my card ,, I wanna ask ,, can I delete nomodeset from grub.cfg after installing the driver ? 

thanks you guys:)

---

### Post by Silvertones on 2010-10-10
I don't think so. I didn't anyway. I've been with 10.04 since April and it has been fantastic. I'm not going to upgrade at all.

---

### Post by anyone2009 on 2010-10-10
thanks again 
good luck :)

---

### Post by sveterv on 2010-10-10
If there are binary drivers for your graphics card, and after installing them they are working fine, probably you can delete "nomodeset". But I'm not sure, as deleting this option in my case switched my system to nouveau (instead of nv) NVIDIA driver, which then were blocking binary NVIDIA driver from even proper installing, so I need to have nomodeset all the time.

But it's not clear at this point to me is it a problem for all people.

Let's say that this way, you can remove nomodeset from grub, and your system should work fine, but if not, put that option there again with recovery mode :)

---

### Post by rudy1094 on 2011-04-06
I'm having trouble with my nvidia graphic card, so I tried the nomodeset option suggested above and when I did I got the attached error message. Any thoughts on what that error means?

---

