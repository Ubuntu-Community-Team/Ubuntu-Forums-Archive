---
title: "Black screen with blinking &quot;-&quot; when installing Ubuntu 12.04 with USB flash"
date: 2013-07-08
forum: Installation &amp; Upgrades
---

### Post by pedrospaulus on 2013-07-08
HI everyone,
Im stucked trying to install ubuntu 12.04 (i've tried both server and desktop version) on my new machine Eebox B202 of ASUS (a netbook like). Since my machine do not have CD/DVD reader, i made a bootable USB stick with unetbootin with another PC thats running windows XP. The bootable USB stick work fine, even when i try it on this machine (my old one that serve to build the bootable USB stick), it propose me all the boot options (install ubuntu, test memories, start from USB etc ...)
But when i try to start  the install of ubuntu on my new machine (Eebox B202 one ) all i get as soon as the USB stick is detected is a black screen with the "-" blinking caracter at the top left corner of the screen. I try to search a little bit on internet, but the problems people describe on forums around the internet are not really like mine. Indeed people talk about "black screen" BUT AFTER passing the install options steps (you know where youre proposed to choose among install ubuntu, test memories, start ubuntu on USB etc ...), but in my case I CANT even reach this step, i get the black screen with the blinking "-" as i start the  machine and it detect the USB stick.
As i read in forums that i visited, may be this is a graphical card driver incompatibility matter, in such case anyone have an idea of what i must do? any way to add something to the USB stick install when making it with unetbootin ( may be a way to add the rigth graphical driver)? or any body have an idea of whrere my problem come from ? any one already installed unbutu on the ASUS Eebox machines?
thanks in advance for your help.

PS: i've already tried differents versions of ubuntu (9.01, 10, 12.04, ...).

---

### Post by sudodus on 2013-07-08
Welcome to the Ubuntu Forums :-)

I suggest you reply to few questions to make it easier to give good advice.

- Does you computer work with any operating system: Is Windows installed and does it work? Have you tried any other linux distro?

- Have you tried with another monitor?

You can try to re-make the boot USB drive such that you arrive at the first syslinux screen, for example cloning the iso file with ***dd*** with help of a shell script. See this link [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

If you arrive at something readable (first the language selector, then the mode selector), you can select boot options with F6 according to this link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

and various boot options.

---

