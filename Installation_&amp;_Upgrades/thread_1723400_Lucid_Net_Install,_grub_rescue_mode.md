---
title: "Lucid Net Install, grub rescue mode"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by abqorian on 2011-04-07
Hi all,
First of all, please excuse my bad English cuz I'm not English.
Second, hope this is the correct place to ask this question, spare my life if it isn't :)

I've been wandering the forum for a while and found a lots of ideas for help. But all of them ask to boot Ubuntu livecd and none prompting about 'no ubuntu cd'.

I've install Lucid via net install on my laptop.
I used unetbootin and chose Ubuntu 10.04 NetInstall because my optic drive was broken (cannot read any dvd or cd) but I have --a slow--internet connection.

So everything went well (including a 2 days installation!) until I boot and a command prompt poped up

```

error: the symbol 'grub_puts_' not found
grub rescue>

```

I've followed [this instruction]("https://help.ubuntu.com/community/Grub2#Rescue Mode"), but when I typed command insmod, it returns
```
unknown command 'insmod'
```

or somethin like that.

So I cannot follow the rest of the steps: insmod, linux, boot.

But the command 'boot' was recognized although it replied 
```
"no kernel loaded"
```

Please help me on this.

As of right now, I tried to boot using USB and get the grub fixed.
Will update soon.

---------
thanks,
Abe

PS: I've Ubuntu 10.04 on desktop PC from which I type this question ^^

---

### Post by wilee-nilee on 2011-04-07
So did you load a thumb with unetbootin then install, or use the netload of unetbootin to install the iso to a partition?

If you have a bootable Ubuntu media, it is difficult to tell from your description to be honest, click on the bootscript in my signature follow the instructions and post all the text from the generated file in code tags. to get code tags open a reply click on the **(#)** in the reply panel and paste all the text between.

Is this a wubi install is my other question? Since you have used a method that as described is hard to figure out at least for me a few questions are needed to get to what's going on.

---

### Post by abqorian on 2011-04-07
Thanks for the reply.

I loaded a thumb with Ubuntu 10.04 NetInstall using unetbootin from a PC. Then boot my laptop using the thumb and try to install it.
The installation then continue using internet connection,.

No, this is not wubi install. I was trying to install Lucid from the internet, since I don't have a working CD drive. I followed an instruction to use netbootin.

---

### Post by wilee-nilee on 2011-04-07
> **abqorian said:**
> Thanks for the reply.

I loaded a thumb with Ubuntu 10.04 NetInstall using unetbootin from a PC. Then boot my laptop using the thumb and try to install it.
The installation then continue using internet connection,.

No, this is not wubi install. I was trying to install Lucid from the internet, since I don't have a working CD drive. I followed an instruction to use netbootin.

So if you had loaded the thumb then unless you had loaded the alternative or minimal install you can get to a live desktop.

Post a link to the instructions you used.

The problem here is that without any way to diagnose your set up by booting a live cd/thumb it is a moot point, if we can't understand what actually happened.

You would not be doing a net install with a loaded thumb unless you used the minimal install iso is this the case here?

Anyway I have to crash see you tomorrow.

---

### Post by abqorian on 2011-04-07
Yes, you are correct. 

I installed my thumbdrive (using unetbootin) a NetInstall version of Lucid. The doc says that unetbootin will install only the minimum system required for booting (I'm guessing it's the most minimum) then continue the installation by downloading from internet.

Thereby the system cannot load the live desktop.

My problem: right after the installation, after booting again, some text popped up on the screen:

```
GRUB loading
error: the symbol 'grub_puts_' not found
grub rescue>
```

so, IMHO the bootloader that is actually corrupted or something.
without being able to get to at least a command prompt properly, I could not even use the script you suggested.

[here's the instruction]("http://www.pcmech.com/article/how-to-install-ubuntu-linux-with-no-optical-drive/").

thanks for your time,

---

### Post by wilee-nilee on 2011-04-07
Okay so since you have no bootable media that goes to a desktop if you know the partition install number you can manually boot in hopefully.

Manual boot from grub prompt for grub2
set root=(hd0,X)    **X=the partition # of OS** 
linux /boot/vmlinuz(tab=kernel) root=/dev/sdaX 
initrd /boot/initrd(tab, then enter) 
boot (enter)

The highlighted portion is just information and the tab notation is for auto completion, and enter means the enter key. Notice the spaces as well, this is not real tricky once you understand it but it was at first for me.

During the install with the minimal you were shown a desktop choice, and other portions of the install, if you get to a desktop run this command in a terminal if the HD is sda.
sudo grub-install /dev/sda
then 
sudo update-grub
Grub will then be installed.

If you didn't install a desktop but get to a command line from the manual boot in run the same commands.

From there you can also install a desktop as well.

---

