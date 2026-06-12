---
title: "Complet newb has question.."
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by mward on 2008-11-27
Hello all, thanks for the help.

I just bought a new Dell Netbook with Ubuntu 8.04 installed. I have a couple of questions:

I found a directory named "examples" with some PDF files in there. To conserve space, I am trying to delete them, but I can't. I right click on the file, choose properties, then permissions and it says "You are not the owner, so you can't change these permissions". How can I delete this file?

Also, can I upgrade from Ubuntu 8.04 to 8.1? Should I?
Can I upgrade from Ubuntu 8.04 to Kubunt 8.1? What is the difference?

Confused in Milwaukee.

---

### Post by andrew.mckevitt on 2008-11-27
I'm sure you could upgrade to 8.10, but if you're new to ubuntu and everything works ok, then maybe there's no need to. At least until you know your way around better. Kubuntu is ubuntu but with a different desktop, KDE as opposed to Gnome in ubuntu. Which is better? Well, It's an ongoing argument.

As to your file permission problem, If you are sure it's not needed then open up a terminal Accssories-Terminal

and type

```
sudo nautilus
```

enter your password when prompted and a file browser will open up with 'root' privilages.
Be warned though, you can 'brick' your netbook quite easily by deleting the wrong things. If you're unsure, don't do it. The PDFs you mentioned, might be worthwhile copying them to a usb stick before deleting them. You never know.

---

### Post by cariboo on 2008-11-27
For graphical applications you should always use **gksu** or **gksudo**, for example if you press Alt-F2 (the equivalent to the run command in Widows) and type:

```
sudo nautilus
```

the command may not work but if you enter:

```
gksu nautilus
```

it will ask for your password and open Nautilus (Places-->Home Folder) as root.

Jim

---

### Post by snova on 2008-11-27
I think you just need to remove the 'example-content' package. Don't delete them manually.

The difference between Ubuntu and Kubuntu is merely that of the default (read: default. You can go from one to the other.) desktop environment that is installed. You may wish to install both, to see which you prefer. (Although it will use a sizeable hunk of disk space.)

---

### Post by crazyness003 on 2008-11-27
This is just a suggestion, but why not use [XFCE desktop environment]("http://www.xfce.org/")? The default of Xubuntu. Take a look at it here [http://www.xubuntu.org/](http://www.xubuntu.org/)

It a lot lighter than both Gnome (ubuntu default) and KDE (kubuntu default). And (i think) takes less space. Like I said, just a suggestion. NetBooks dont have the most SSD space.

Remember: (Xu)(Ku)(U)buntu is still Ubuntu. Thats the Operating system, that makes everything work. Linux is the kernel of the operating system (kinda like the NT kernel for windows NT, 2000, XP etc). The DE (desktop environment) can be anything you like. Even just a terminal (kinda like in ubuntu server edition). So this gives you limitless posibilities on customizations.

If you're not too farmiliar with everything, id stick with what you already have. But if you ever feel adventerous, try the different DE's or WM's (window managers) out.

---

### Post by inobe on 2008-11-27
my personal opinion, don't upgrade, don't switch to kubuntu, don't delete important system files!

8.04 is an lts version, it is still supported and very stable, it would not make any sense to upgrade' "unless of course you wish to test and release bug reports", many will argue with that last quoted statement i made........

if you are not sure what a file is for, don't delete it.

your current desktop "gnome" is fully customizable, if you wish to change the look' ask in **Desktop Effects & Customization** forum.

---

