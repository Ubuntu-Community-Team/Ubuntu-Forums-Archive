---
title: "Noob: After stage1 and reboot"
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by hellan on 2005-08-01
Hello Ubuntuusers!

Just tried to install ubuntu. Ive inserted the cd, completed the instructions for stage1 as choosing partions and all that. No problems really.
So then it tells me Ive completed stage1 and I need to remove the cd for reboot.

So it reboots and I end up in the terminal. I have two new mails that tells me about debconf. I should use this program to continue install ubuntu. But I dont know how to use debconf. Just using debconf, gives me a return answer that I need to write more than just "debconf". 

I read this in Userdocumentsection on the ubuntuhomepage.
[https://wiki.ubuntu.com/Installation/I386](https://wiki.ubuntu.com/Installation/I386)

"Install a boot loader

If the installer detects other operating systems on your computer, it will add them to the boot menu. 

The installer will now tell you that the first stage has finished. 

Remove the CD and hit Enter to reboot your machine. It should boot up into the second stage of the installation process"



Well is doesnt boot up into the second stage of the installtions process. It leaves me hangin in the terminal.
Ive asked on the ircchannel. I guy told me to "sudo apt-get install ubuntu-desktop".
But I guess that doesnt really give me any chance to choose which packages I want and so on. Is this the only alternative or is there any way to do this "the right way"?

Thankful for your help
Noob Robert

My computer:
Intel Celeron 450MHz@525
160Mb Ram
Voodoo3 3000
Root partion is 3Gb
256Mb Swapspace

---

### Post by GavinX on 2005-08-01
That may be the best way to proceed and when you have installed the packages, just remove and add as you se fit. It's a little strange that the installation did not continue on its own. However, I suspect that this is not a great problem. Also, if you wanted to select packages what you should have done during the initial install is to choose expert mode, that would have given greater control over the installation. Of course, you woud have to know just what you are doing as it is not recommended for new users. That is why a a particular mix of software was preselected; it's designed to assist the new and inexperienced user.

Cheers,
GavinX

---

