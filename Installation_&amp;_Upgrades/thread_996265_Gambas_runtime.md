---
title: "Gambas runtime"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by UpsideDownFace on 2008-11-28
I have installed Gambas2 via System=>Administration=>Synaptic Package Manager. Applications=>Programming now has Gambas2 which i ran and wrote a program with a single form, a label saying "Hello", a button with "OK" on it.
This works on the computer with the Gambas Design System, but I want to write programs which I can send to computers that don't have Gambas installed.
So I copied the resulting program via a thumb-stick to another computer, where the program totally failed to respond to a double click.
An e-mail to "gambas@sourceforge.net" produced the reply that because Gambas is interpreted it must have the "Gambas-Runtime" installed.

I have not been able to find how to install gambas-runtime on a computer which doesn't have gambas in full.

"Synaptic Package Manager"=> Search for gambas-runtime allows me to install it, but it doenn't work.
"which gbr2" gives "/usr/bin/gbr2" which looks whit I would expect.

Gambas seems to be what I want for quick GUI program development, but is not much use if I can't distribute the programs!

I have struggled in the past with Visual Basic and VB.NET but Gambas seems much better, and doesn't have the handicap of needing an operating system I abandoned several years ago.

Can anybody help please?

---

### Post by UpsideDownFace on 2008-11-29
I have found the answer to my problem.
After opening gambas2 and writing a program,
A. to work on the machine it was written on, in the menu at the top of the gambas2 screen "Project=>Make=>Executable" has to be chosen, and the instructions followed about where and what you want.
B. to make something that can be transferred to a machine without gambas,
under "Project=>Make=>Installation Package" there are several windows which follow, for setting
 1.Package Information. here I just clicked "Next", because I didn't know what is best.
 2.Changelog. Type something mildly meaningful into the upper box on this screen. It looks as if it is just saved in a log. Then click "Next"
 3.Target distribution. This has 7 boxes for the different distributions you may wish to provide for. On my computer 4 are grayed out(for Fedora,Mandriva,SUSE,Slackware), with a message like "rpmbuild is not installed on your system". I ticked a box in the "Ubuntu" section, but there are also "Debian" and "Autotools". then clicked "Next"
 4.Package group.This has a tree-like list of things like "Archiving" Books" "Development". If you don't choose one you are told you have to. I chose "Toys" because it was highlighted and I don't know any better. then click "Next".
 5.Menu entry. Again, "Toys" was highlighted, so I clicked "Next"
 6.Destination directory. At last something I understand, with a tree of my home directory. I had already created a directory in anticipation, so I highlighted it, and clicked "Next"
 7.Create package. The "OK" button tells it to get on with it, and the panel has a scrolling display which looks like the output from a Makefile,

First time, the last line was "Package .... has failed", with a line earlier saying "Source package name contains illegal character 'H' "

So I went back to the start and made a new project with a name in lower-case.
This time the last line was "The packages have been successfully created" and a small window said "Close" or "Retry".

Now in the chosen directory there was a zipped-file icon with the <program name> + "_0-0_i386.deb", so I copied that onto a USB stick which I plugged into my "computer-without-gambas"

On the computer-without-gambas a directory of the USB stick appeared soon after I plugged it in.
I then double clicked on the icon, and it got on with installing. After a while I chose "Applications" from the Ubuntu menu, and "Other" showed <program name>.

Clicking "Applications=>Other=><program name>" made the program run. so YIPPPEE.

I think gambas2 is dead-good for quick simple programs, and the language documentation is also dead-good, but the system documentation might be dead-good-or-bad, but I couldn't find it.

So if anybody wants to use gambas, get gambas2, and run it on just one computer.

---

