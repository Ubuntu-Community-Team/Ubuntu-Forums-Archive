---
title: "upgraded to 10.04, reboot fail"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by radiomog on 2010-05-05
looks like everything upgraded like the other upgrades I did on a couple other machines this weekend, but upon reboot, I get a mouse pointer (inop) and the little 'drum beat' audio file plays, and it goes into a loop (blank screen, pointer, audio...(repeat)...)

upgraded from 9.10 (both old and new versions are the x64 version) (my successful upgrades to 10.04 were on both x86 and x64 versions)
Lenovo T400

dual boot w/ xp (grub seems to work just fine)

I checked the menu.lst (~) for proper kernel versions as mentioned in another post, and they looked correct to me.

anything I should be looking at?

---

### Post by radiomog on 2010-05-17
update: the cursor does in fact, move.. but everything else is the same..

can anyone recommend something? maybe some words to search  with... I'm not finding much luck of similar problems :(

tnx

---

### Post by kansasnoob on 2010-05-17
Have you tried booting into recovery mode?

If it completes you should see the options:

resume
clean
dpkg
failsafeX
grub
netroot
root

If you get that far select "resume".

You'll then have to enter username and password when prompted, and finally type startx.

Then we'll keep our fingers crossed :)

---

### Post by kansasnoob on 2010-05-17
If you get as far as seeing those options, and "resume" fails, I'd next try failsafeX.

FailsafeX is basically the same as "safe graphics mode" so it's not a true solution but just a step in figuring things out.

---

### Post by kansasnoob on 2010-05-17
Another thought, since you mention menu.lst you must still have legacy grub so this may (or may not) apply:

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Upgrading](http://www.ubuntu.com/getubuntu/releasenotes/1004#Upgrading)

> **GRUB menu.lst: install the maintainer's version vs. keep the local version**

If you have previously modified the menu.lst bootloader configuration for GRUB, either by hand or with a tool such as kgrubeditor, you may be asked on upgrade whether you wish to keep your local version of the menu.lst or install the package maintainer's version. This question is asked because such changes cannot be merged automatically with 100% reliability, and care is taken to not overwrite the user's manually edited bootloader configuration without warning.   

However, if you choose to "keep the local version currently installed," your system will not be set up to boot from any newly-installed kernels. Manual action is required on your part to ensure that your system is running the current, security-supported kernel after upgrade. If you have local changes to your bootloader config that you want to keep, it is recommended that you follow these steps:   

    * Choose "keep the local version currently installed" at the prompt.  
    *

      Open /boot/grub/menu.lst with a text editor (e.g., sudo gedit /boot/grub/menu.lst).  
    *

      Apply any changes you've made to the kernel boot options to the commented variables (e.g., groot, kopt, defoptions) above.   
    *

      Move any manually-added boot options for other operating systems so that they are above the line   

      ### BEGIN AUTOMAGIC KERNELS LIST

      or below the line   

      ### END DEBIAN AUTOMAGIC KERNELS LIST

       
    *

      Save the file, and run sudo update-grub from the commandline.  
    * Choose "install the package maintainer's version".   

For example, if you added an option i915.modeset=0 to the "kernel" line:   

kernel          /vmlinuz-2.6.31-14-generic root=UUID=0e7... ro quiet splash i915.modeset=0

then add this option to kopt:   

# kopt=root=UUID=0e7... ro i915.modeset=0

An updated version of the grub package will include information about this problem in the help screen for the menu.lst prompt. (470490)    

---

### Post by radiomog on 2010-05-17
> **kansasnoob said:**
> If you get as far as seeing those options, and "resume" fails, I'd next try failsafeX.

FailsafeX is basically the same as "safe graphics mode" so it's not a true solution but just a step in figuring things out.

thanks... I was able to do this and get to startx, I got the welcome sound and saw my desktop image, but it dropped out of that and all I got was a cascading terminal prompt...  I was able to issue a restart command from here (although I couldn't really see what I was typing) and went in to try the failsafex and am in there now probing around... (I DO have a desktop, but I was presented with an error message about module "dri" not existing)

thanks for the help, I will see what I can do from here!

---

### Post by radiomog on 2010-05-19
I think this is now a aticonfig problem.. no adapters found.. ati software isn't working... and I see that I'm not alone when it comes to this issue.

---

