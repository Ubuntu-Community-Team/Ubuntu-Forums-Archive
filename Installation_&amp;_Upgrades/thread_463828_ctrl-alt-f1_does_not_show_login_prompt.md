---
title: "ctrl-alt-f1 does not show login prompt"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by dan-arwed on 2007-06-04
Hi all,

I got a strange problem concerning console logins. If I try to switch to a terminal, ctrl-alt-fn where n may be any of numbers [1,6], I only get a "weird" screen, which looks like some very fuzzy picture.
But I don't get the login prompt. This is the same at login screen. If choose there "session type: console", I won't be able to see the login prompt. Starting a terminal in KDE (alt-f2 + conlole), the console is
"rendered" sufficiantly and logins are possible. 

My system is Feisty Fawn installed on an IBM Laptop with ATi Radeon X1400 grpahics card. I installed the linux driver provided from ATi (Unfortunately I do not know if the console login worked before the driver installation).
I am reilly helpless, for I do not know which config files I shall check, and for I didn't find neitherr any help in the net nor anyone who had the same problem.

Hoping anybody could give me some suggestions I send my greetings to this great forum

Dan

P.S. In the logfiles /var/log/messages, dmesg, Xorg.log there was no hint at all. If encessary I will post them, too.

---

### Post by dan-arwed on 2007-06-04
Hi there,

I figured out that I am able to login in a console (by the "who" command in a KDE-console),
but I still do see only the fuzzy picture...

Found in another post 

[http://ubuntuforums.org/showthread.php?t=457926](http://ubuntuforums.org/showthread.php?t=457926)

that /etc/event.d/tty - files were damaged, which is not the case with me as far as I can see.
in the post reinstalling system-services was proposed, shall I try this?

Thanks for any help, I'm at my wit's end 8-(

Dan

---

### Post by dan-arwed on 2007-06-04
Salut @all,

After hours =) of searching I found this post:

[http://ubuntuforums.org/showthread.php?p=2384663](http://ubuntuforums.org/showthread.php?p=2384663)

where another user had similar problems like me. I tried to switch off the 
LCD HV expansion in the BIOS. The result was not sufficient, the console has now higher 
solution, but the weird fuzzy screen still appears. 

Fortunately, setting the option vga=791 (1024x760) in /boot/grub/menu.lst
helped me out. Now that it works I will try to understand it better 8-)

Regards!

---

