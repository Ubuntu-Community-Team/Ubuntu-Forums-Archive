---
title: "No login prompt 16.04 mini iso/server install"
date: 2017-02-12
forum: Installation &amp; Upgrades
---

### Post by verymadpip on 2017-02-12
Hi everybody.
I've a couple of old/low end machines I'm trying to keep alive using minimal installs:
MSI U180 netbook: N2600 Atom CPU GMA3600 graphics, 2Gb RAM
&
Compaq CQ58 Presario: AMD E300 APU with Radeon HD graphics, 4Gb RAM. (Might need taking apart & cleaning).

When I try an install from either the 64 bit 16.04 mini.iso or 16.04.1 64 bit server all I reboot to is a black screen with a blinking cursor in the top left corner.
ctrl+alt+f1 - f6 does nothing.  I simply cannot login to the install to add a window manager or anything else.  I'm sure I've got the bootloader on the correct device (made that mistake before), but really am at a bit of a loss.

Installing from a normal medium (Lubuntu 16.04.1 64 bit for example) results in a proper installation which works as expected.

It's not a massive deal, as I've got working Lubuntu installs going but if anyone has any ideas about what's happening I'd appreciate the input greatly.
(I've found working from minimal installs a good way to learn stuff & I think the Compaq particularly would benefit from running something as light as possible).

---

### Post by DuckHook on 2017-02-13
From one tinkerer to another, here are some ideas, culled from long nights wrestling with just such problems as yours:

[list=1]
[*]When Tasksel comes up during the install process, choose "SSH Server" as one of your desired packages. Even if the post-install video is borked, you will still be able to ssh into your balky machine from a working machine on the network to either finish what you are doing, or wrestle with the problem.

[*]When booting up one of your balky machines, try adding the nomodeset kernel parameter at the GRUB command line. This solves some boot issues, but not all.

[*]Since a graphical install works, try looking for the settings that make it work with the usual:```
lspci -vk | grep -iA13 vga
```…and see what driver Lubuntu is using. Also look at the successful /etc/default/grub to see what differences there are with the non-working one (this assumes you are able to ssh into it).
[/list]
FWIW, your machines are not all that old/low end. The Presario is admittedly underpowered, but it has a lot of RAM going for it, which is very valuable in the 'buntu world. I agree with you that starting from a very minimal base is just what is needed for laptops like yours.

If you can successfully SSH into your blind machines, then you can either chase down the issues for curiosity's sake, or you can try installing either lubuntu-core, ubuntu-mate-core or xubuntu-core. These selections will install an absolute minimal version of their associated desktop without any of the productivity apps. If that's all you are interested in, a successful install might render the graphics problem academic. My personal preference would be to wrestle the problem to the ground, but I'm odd that way. Of course, if your goal is to use these things as CLI-only servers, then you don't want any GUI on them at all, which means wrestling with the problem is a practical measure.

You may also find the link in my sig: *Resurrecting Old Hardware* to be of help.

---

### Post by verymadpip on 2017-02-14
Hi DuckHook.
Thanks for the tips & info.

Currently the MSI works well with Lubuntu - I'm going to leave that alone for now.
I'm running the Lubuntu openbox session on the Presario with a couple of simple tweaks & it seems to have helped performance somewhat.

SSH is a bit above my pay grade at the moment, but is one of those learning opportunities I mentioned :)
Neither box is a "production" machine so I'm going to take my time with this "project" & see how I go on.

Expect many more questions & thanks again.

---

### Post by sudodus on 2017-02-14
You can also take a shortcut and try to install a text mode system from a compressed image file (that was originally created from Ubuntu mini.iso. You find it at this link,

[dd_X32-Txt-Startx-Intl_2016-12-11_4GB.img.xz](http://phillw.net/isos/linux-tools/compressed-images/dd_X32-Txt-Startx-Intl_2016-12-11_4GB.img.xz)

The [compressed] size is only 368 MiB and you can check the md5sum like the following,

```
$ md5sum dd_X32-Txt-Startx-Intl_2016-12-11_4GB.img.xz
07e6767e8715b22e32f848c2f22d9e9b  dd_X32-Txt-Startx-Intl_2016-12-11_4GB.img.xz
```

[B]user: guru
password: changeme[/B]

[hr][/hr]
This system is described briefly with screenshots at this link,

[Compressed image of an installed 32-bit Xenial mini system with dus](https://ubuntuforums.org/showthread.php?t=1958073&page=30&p=13584352#post13584352).

This system is made to work in old computers. It does not need much cpu horsepower and not much RAM. You can install it with [mkusb](https://help.ubuntu.com/community/mkusb) into an internal drive or a USB pendrive (or a memory card, if your computer can boot from a card adapter).

---

### Post by verymadpip on 2017-02-16
Hi sudodus & thanks for the info.
I don't want to come over as an ingrate but, I was hoping to use a 64 bit OS so I can install google chrome for Netflix.
Both boxes, although a little underpowered are capable of streaming Netflix with no real issues.

I should probably look into running 64 bit chrome on a 32 bit OS.
64 bit chrome on  a 64 bit OS just seemed a little less work. Mind you, this is turning into a little project & that whole idea could be yet another useful learning experience.

Thanks again.

---

### Post by sudodus on 2017-02-16
I thought you wanted a 32-bit system for that old computer. Anyway, there are corresponding compressed image files with 64-bit Ubuntu, that can boot both in UEFI mode and BIOS mode. These systems were made from an Ubuntu Server iso file. See this link,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

You are welcome to use one of these compressed image files, or if you prefer, just get some inspiration from the method I have used and build your own system. Good luck with your little project :-)

---

### Post by DuckHook on 2017-02-16
> **verymadpip said:**
> …SSH is a bit above my pay grade at the moment, but is one of those learning opportunities I mentioned :)

@verymadpip

In the spirit of another learning experience:

*tasksel* could not be easier to use. If doing either a mini.iso or a server install, it naturally comes up at a certain point during the initial install process and looks like this:

[ATTACH=CONFIG]273749[/ATTACH]

It gives you a variety of further package choices.

[list=1]
[*]All you need do is select "OpenSSH server" in addition to the default "Basic Ubuntu server". SSH server will then install automatically.
[*]To SSH into your blind machine, using another machine on the same LAN, just do```
ssh username@hostname_of_machine
```…replacing both username and hostname_of_machine with those you set up in your initial install. SSH will ask for your password. Once typed in, your machine will ask if you want to add the new connection to your list of known hosts. Answer "yes", and voila: you are connected over a secure encrypted channel. You can now use your blind machine as if you were typing directly into it.
[/list]
sudodus's method is very easy. But it's good to know about the SSH workaround too.

---

### Post by sudodus on 2017-02-16
... or combine both methods. 'My' compressed images give you systems, where ***tasksel*** is available via the text mode menu, as illustrated in this link (scroll down to the pink menus),

[Mini system with 'text' screen user interface](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#Mini_system_with_.27text.27_screen_user_interface)

II agree with DuckHook: it is very convenient to communicate between computers with ssh: log in remotely via ssh and transfer files via sftp, or use some GUI application which can do the corresponding tasks.

---

