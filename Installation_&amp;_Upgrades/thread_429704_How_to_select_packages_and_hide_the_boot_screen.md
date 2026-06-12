---
title: "How to select packages and hide the boot screen?"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by kustodian on 2007-05-01
I am an old Slackware user :cool:  

And I installed Kubuntu so I could see how easy it is to install (and I wanted to see Beryl, Slack has old x.org 6.9 ](*,) ).
The installation is very easy, too easy if you ask me. I was disappointed to see that I can't select which packages are going to be installed :shock: 

So my first question is: Is there a way to select which packages are going to be installed during install?

My second question is related to the boot screen during the boot of linux (not the kde splash).
Is there a way I could hide it, by pressing a key or something else (I know I could change the boot parameters in the Grub configuration)?

Thanks in advance and great job with Feisty =D>

---

### Post by Rinzwind on 2007-05-01
Regarding 1st question:
Nope. It installs like it is. Changes you do after the install. I have a few script files ready to remove whatever I don't want and whatever I need to add ;)

Regarding grub:
sudo kate /boot/grub/menu.lst 

change:

> 
<..>
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"][/COLOR]**hiddenmenu**[/color]

# Pretty colours
#color cyan/blue white/blue
<..>

You press a key (ESC) to show grub not the other way around. (but you seem to allready know how to do that ;) )

---

### Post by kustodian on 2007-05-02
> **Rinzwind said:**
> You press a key (ESC) to show grub not the other way around. (but you seem to allready know how to do that ;) )

You didn't understand me, I meant the blue Kubuntu splash screen which is shown while the linux is being loaded, is there a key on the keyboard I could press so I could see what's being loaded, or the only way to hide it is to change boot parameters it in Grub?

---

