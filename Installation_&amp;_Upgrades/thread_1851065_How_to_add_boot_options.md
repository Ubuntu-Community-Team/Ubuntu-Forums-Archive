---
title: "How to add boot options"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by Juan Largo on 2011-09-27
I've been using Linux for about 5 years and it is my main operating system.  I have a question that I can't find the answer to.  Before you tell me to RTFM, let me assure you that I have searched these forums, done a thorough Google search, and read through the GRUB2 manual.  

Here's the question:

How do I include the cheat code "VGA=789" when booting with GRUB2?  

I need that cheat code to prevent a loss of signal to my monitor while I boot Kubuntu 10.04.3.  Otherwise, my monitor shuts off.  I can add the cheat code when booting the Live CD, but I don't know how to include the cheat code *after* I install Kubuntu on the HDD.

With legacy GRUB, all I had to do is open menu.lst in a text editor, type in the cheat code on the boot line, and save the file.  With GRUB2, menu.lst is gone and from what I've read, I'll have to write some sort of computer program in order to make any changes to GRUB2.  

Please don't give me the usual responses about how much better GRUB2 is compared to classic grub, or how I must learn an esoteric computer language in order to keep up with everybody else.  I'm not a computer programmer, and I'm too old (67 years) and don't have the time or patience for writing elaborate scripts to do simple things like this.  I just want it to add a simple boot code without having to get a college degree in computer programming.

If you can help an old guy like me, thank you in advance.  If you can't offer help, please refrain from posting comments.

Yours truly,

Juan Largo

---

### Post by matt_symes on 2011-09-27
Hi

You need to add it to the grub command line ? If that is the case then open a terminal.

Type

```
sudo nano /etc/default/grub
```

to start nano editing the grub file.
Enter your password. It will not be echoed to the screen. This is normal.

Scroll to the line that looks something like

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and change it to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash VGA=789"
```

Press ctrl and o at the same time to save and ctrl and x to exit nano.

After that type

```
sudo update-grub
```

When grub has been updated, reboot.

Kind regards

---

### Post by Juan Largo on 2011-09-27
@ matt_symes

Thank you very much for your help.  

I would need to run the commands you posted from the Live CD in the rescue mode, because without "VGA=789" boot code already included, my monitor would be off (no signal).  So this brings up another question:  How do I run the final command "sudo update-grub" from the Live CD in order to update GRUB on the HDD?

I have one final question:

If I use the "VGA=789" cheat code with the Live CD when I install Kubuntu, would the installer carry the cheat code over to GRUB2 in the final installation?  If it does, then my problem is solved.

---

### Post by MAFoElffen on 2011-09-27
> **Juan Largo said:**
> @ matt_symes

Thank you very much for your help.  

I would need to run the commands you posted from the Live CD in the rescue mode, because without "VGA=789" boot code already included, my monitor would be off (no signal).  So this brings up another question:  How do I run the final command "sudo update-grub" from the Live CD in order to update GRUB on the HDD?

I have one final question:

If I use the "VGA=789" cheat code with the Live CD when I install Kubuntu, would the installer carry the cheat code over to GRUB2 in the final installation?  If it does, then my problem is solved.
You have 2 options:

Option 1:
Bring up Grub Boot menu by repeated pressing the shift button while booting... At the Grub boot menu, press "e" to put it into an edit mode.  Arrow down to the line starting with "linux" which is the kernel boot line, go to where is says "ro quiet splash" and add your "vga=789" kernel boot switch. Press <cntrl><x> to boot.  Make the changes in /etc/default/grub to make it persistent.

Option 2:
Boot from LiveCD. Mount your system usiing the chroot instructions in the second half of post   			#[**3**]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3") of my stcky.  Those instructions were for mounting a sys and installing drivers, but can be used for grub also... Set #5 for you would be:
```

gksudo gedit /etc/default/

```
Make you changes adding your kernel boot switch, then
[code]
sudo update-grub
[code]
Refer to posts 1-3 for reference and instructions:
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

---

### Post by MAFoElffen on 2011-09-27
> **Juan Largo said:**
> I have one final question:

If I use the "VGA=789" cheat code with the Live CD when I install Kubuntu, would the installer carry the cheat code over to GRUB2 in the final installation?  If it does, then my problem is solved.
Wait. it's not installed yet?

Follow the instructions on the first half of post 3 of my sticky to change the boot options of the LiveCD...  The install routine "will not" carry over the "kernel boot option" (not referred as a cheat code") to Grub during the install...

So you will still need to make it persistent using the instructions I gavee you in the last post.

---

### Post by Juan Largo on 2011-09-27
> **MAFoElffen said:**
> Wait. it's not installed yet?

Follow the instructions on the first half of post 3 of my sticky to change the boot options of the LiveCD...  The install routine "will not" carry over the "kernel boot option" (not referred as a cheat code") to Grub during the install...

So you will still need to make it persistent using the instructions I gavee you in the last post.
You are correct.  I have not installed Kubuntu *yet*; however, I know that I'll need to include "VGA=789" in order to get a signal to my monitor, so I'm planning ahead.

I understand your instructions.  Option #1 (hitting the Shift key repeatedly) will allow me to add the cheat code that permits me to boot into Kubuntu.  Then I can use the instructions posted by you and matt_symes to modify GRUB2 after booting from the HDD.

Option #2 (using chroot to modify GRUB2 from the Live CD) would also work, but I think it would be a little easier to do it using Option #1.

Thank you for pointing out that the cheat code entered on the Live CD will *not* stick in the final installation.  So I know I'll have some work cut out for me in order to complete the installation.

I believe the problem is solved.  Now I just need to get to work.

Thanks a million for your help.

btw - I like Kubuntu very much and I look forward to making it my primary operating system.

Yours truly,

Juan Largo

---

### Post by mörgæs on 2011-09-27
Good. If the problem is solved, please mark the thread so using 'thread tools'.

---

### Post by oldfred on 2011-09-28
With grub2 VGA= is obsolete.

vga=xxx is a deprecated boot option
Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)
"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)

VGA conversions if you do not know mode:
[http://wiki.archlinux.org/index.php/Gensplash](http://wiki.archlinux.org/index.php/Gensplash)
[http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)

---

