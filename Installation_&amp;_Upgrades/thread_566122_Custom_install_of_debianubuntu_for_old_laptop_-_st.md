---
title: "Custom install of debian/ubuntu for old laptop - still too slow"
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by __knk__ on 2007-10-03
hi all, ive recently acquired a free laptop (acer travelmate 220) with a busted harddrive.  fixed that now and all is good.  however i cant seem to get decent performance in any configuration i try.  ive tried ubuntu lite and wasnt really fast enough especially using firefox however in windows xp i have no problems with this.  at the moment im using a custom base install of debian etch which i just used apt-get on to get the programs/utils i wanted.

specs are:
1ghz celeron(nasty i know lol)
80gb wd scorpion 
128mb ram(sd i presume)

i really wanted to run xfce but that seems out of the question, fvwm-crystal fluxbox and icewm seem to run best out of everything ive tried however i still have alot of problems with speed.

the main reason im posting this is because i got better performance using windows xp which is a first for me


this is mainly for web browsing/msn(gaim).  hmm what should i try now?

thanks

---

### Post by kaar3l on 2007-10-03
Elive, seems to be fast and beautiful, i haven't tried it by myself. :)
[http://distrowatch.com/table.php?distribution=elive](http://distrowatch.com/table.php?distribution=elive)

---

### Post by kerry_s on 2007-10-03
> **__knk__ said:**
> hi all, ive recently acquired a free laptop (acer travelmate 220) with a busted harddrive.  fixed that now and all is good.  however i cant seem to get decent performance in any configuration i try.  ive tried ubuntu lite and wasnt really fast enough especially using firefox however in windows xp i have no problems with this.  at the moment im using a custom base install of debian etch which i just used apt-get on to get the programs/utils i wanted.

specs are:
1ghz celeron(nasty i know lol)
80gb wd scorpion 
128mb ram(sd i presume)

i really wanted to run xfce but that seems out of the question, fvwm-crystal fluxbox and icewm seem to run best out of everything ive tried however i still have alot of problems with speed.

the main reason im posting this is because i got better performance using windows xp which is a first for me


this is mainly for web browsing/msn(gaim).  hmm what should i try now?

thanks


have you done any fine tunning?

web browsing, have you tried opera.
/etc/apt/sources.list repo & key
```

# su
# gpg --keyserver subkeys.pgp.net --recv-key 6A423791
# gpg --armor --export  6A423791| apt-key add -
deb http://deb.opera.com/opera/ etch non-free 

```

gaim,pidgin = give ayttm a try

```
**apt-get install ayttm**
```

put this in /etc/sysctl.conf(reboot)

```
[B]
vm.overcommit_memory=2
vm.overcommit_ratio=70
[/B]
```

hold on i'll get back to you. :)

---

### Post by kerry_s on 2007-10-03
okay, you must be doing something wrong. 128ram is perfectly usable with xfce4. i just cut my ram in half(256 to 128) and it still runs just as fast as 256ram. i also only have half the cpu you have(450mhz).

what did you install from the base?
i use> apt-get install xorg synaptic xfce4 xfce4-appfinder

then i reboot, login & startx, then open synaptic and keep building.

---

### Post by __knk__ on 2007-10-03
elvie looks nice but i wanted to stick with debian or ubuntu, ill give it a try if the recommendations on here dont go as planned.  ill try the fine tuning now, and let u guys know how that goes.  ive installd the same things as recommened by kaarl37.  after the fine tuning ill start from a base install of debian 4.0 etch/stable.  thanks for all the help...im gonna stick to getting xfce to run.  if i can run windows xp comfortably then i shud be able to run xfce4, im actually posting off it now:)

---

### Post by __knk__ on 2007-10-03
okay so the memory tweak didnt make as much of a difference as id hoped, ive just started installing stable now, when it asks for me to pick what type of system to install ill just leave em blank and then apt-get install xfce4 xorg to get a base system.  then just edit my xorg.conf as the video card doesnt work with the vesa driver which is weird...tell me if ive done anything wrong :)

edit: didnt notice elive was based on debian so i guess i can use the same repos?, ill try it out if this doesnt go too well

---

### Post by __knk__ on 2007-10-03
how did u get ur ram usage so low kerry_s i did a base install with absolutely nothing and then apt-get install xorg xfce4 and im at 93mb lols.:(

---

### Post by kerry_s on 2007-10-03
> **__knk__ said:**
> how did u get ur ram usage so low kerry_s i did a base install with absolutely nothing and then apt-get install xorg xfce4 and im at 93mb lols.:(

it's suppose to use ram, unused ram is wasted ram. the longer it stays in ram the faster the application will launch the next time. on this old laptop(pcg-f430) it does this thing were it likes to move from ram to cache.

the thing is your system shouldn't be slow though.

i want you to try these.
```
[B]su
mousepad /boot/grub/menu.lst
add
elevator=deadline pci=routeirq

to the end of your kernel
looks like this->
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/hda1 ro vga=791 elevator=deadline pci=routeirq 
[/B]
```

do you want autologin?
```
[B]mousepad ~/.bash_profile
at the bottom put->

if [ `tty` = "/dev/tty1" ]; then
startx
fi

that will startx after you log in
this will log you in->

su
apt-get install mingetty
mousepad /etc/inittab
replace

1:2345:respawn:/sbin/getty 38400 tty1
with
1:2345:respawn:/sbin/mingetty tty1 --autologin user

(replace "user"  with your login name)
[/B]
```

reboot
let me know how that works out.

---

### Post by kerry_s on 2007-10-03
when you get around to it, i'd like to see a screen shot of your terminal with top.

to set up

[B]su
apt-get install scrot
[/B]
then open your keyboard settings> shortcuts

click add on the left, name it what ever you want, mine is "mine"
click add on the right
for the command put> scrot %T.jpg
press the print button.

then just open your terminal type> top
press print
and attach

---

### Post by kerry_s on 2007-10-03
> **__knk__ said:**
> okay so the memory tweak didnt make as much of a difference as id hoped, ive just started installing stable now, when it asks for me to pick what type of system to install ill just leave em blank and then apt-get install xfce4 xorg to get a base system.  then just edit my xorg.conf as the video card doesnt work with the vesa driver which is weird...tell me if ive done anything wrong :)

edit: didnt notice elive was based on debian so i guess i can use the same repos?, ill try it out if this doesnt go too well

for the memory tweak try 1
( vm.overcommit_memory=1)

2 is new, it's only in 2.6 kernels, but it doesn't seem that great. i've moved mine back to 1. the values are 0(default) 1 and 2, 2 is the newest setting.

---

### Post by __knk__ on 2007-10-03
alritey, so ive tried all the tweaks you gave me and got the screenshot with top.  all in all theres a pretty noticable difference in speed dont know exactly where its coming from but still good none the less.  the only thing i have grief with is the speed of the browsers really now as they seem to be a heap slower than their equivalents in windows xp however this might all be in my head or something.  ive started using opera as u sugested and theres a noticable improvement there, i might give swiftfox a try and see how that goes:).  tell me what you think about the screenies

---

### Post by __knk__ on 2007-10-03
thanks a heap for that vga line in the kernel aswell, i couldnt switch between alt+f1-f7 etc

---

### Post by kerry_s on 2007-10-04
okay, that looks good.
a few observations, next time, go with a gig of swap, since you have small memory. xterm is lighter than xfce4-terminal and is already installed.
firefox is always slow to start, can't do nothing for that.


lets do your sudoers now.

su
visudo

add->
```

your-name  ALL=(ALL) ALL
%nopasswd ALL=(root) NOPASSWD: /usr/bin/conky, /sbin/halt, /sbin/reboot, /sbin/shutdown, /usr/sbin/xfsm-shutdown-helper, /usr/bin/thunar, /usr/bin/mousepad, /usr/sbin/synaptic

```

in terminal> sudo addgroup nopasswd
gksudo mousepad /etc/group

add yourself to the nopasswd group


now you should be able to use sudo and you can use certain gui apps with out a password. synaptic won't ask for a password, neither will shutdown. so make sure you have prompt check so you get the shutdown options.

the thunar and mousepad are for your custom actions. for unpacking things i use unp(apt-get install unp) it's super light.

i'll try and think of more tips for you, i can't find my notes. :confused:

---

### Post by __knk__ on 2007-10-04
looks all very nice:) thanks soo much. its a little laggy but its usable now, i did about an hour and a half of msning on it earlier today however when opening firefox or opera at teh same time it lags, not just the opening time but afterward while using it.  a mate recommended epiphany but i found it pretty shitty last tiem i used it.  battery wen dead before i tried it out tho lols using my desktop now. ill try it tomorrow.
ill add the sudoers later, altho i usually just use su sounds helpful for synaptic etc

why use 1gig swap? considering the 512 is barely being touched?unless im missing the point:p

appreciate the help alot very usable now:)

---

### Post by kerry_s on 2007-10-04
> **__knk__ said:**
> looks all very nice:) thanks soo much. its a little laggy but its usable now, i did about an hour and a half of msning on it earlier today however when opening firefox or opera at teh same time it lags, not just the opening time but afterward while using it.  a mate recommended epiphany but i found it pretty shitty last tiem i used it.  battery wen dead before i tried it out tho lols using my desktop now. ill try it tomorrow.
ill add the sudoers later, altho i usually just use su sounds helpful for synaptic etc

why use 1gig swap? considering the 512 is barely being touched?unless im missing the point:p

appreciate the help alot very usable now:)

512 is okay, but if you do run in to trouble, you can->
**apt-get install dphys-swapfile**

---

### Post by ArtF10 on 2007-10-04
This is related .... I think.  How would one tell ubuntu to use more "swap"  if that makes any sense...I have 2GB RAM and would like Fiesty to use that to speed up the responsiveness/boot up time of the system.

---

### Post by kerry_s on 2007-10-04
> **ArtF10 said:**
> This is related .... I think.  How would one tell ubuntu to use more "swap"  if that makes any sense...I have 2GB RAM and would like Fiesty to use that to speed up the responsiveness/boot up time of the system.

it don't work that way. swap is slower than ram, you should be fine with 2gig.
you could get away with no swap at all.
i'm guessing your using gnome for your DE, you can go lighter which would be faster, for example using xfce4 instead(sudo apt-get install xubuntu-desktop) personally i would do a clean install i hate mixing DE.

xubuntu-> [http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/)
debian-> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

i find debian faster and more stable, but it's your choice.

---

### Post by ArtF10 on 2007-10-04
I've been using XFCE in Zenwalk and it is lightning fast but I've always wanted Gnome to run faster and after  googling, reading and following "10 ways to make Ubuntu faster" I seem to understand that swap would be faster?  Anyways, I guess I'll just have to live with what I have since a custom install went ballistic on me.

> **kerry_s said:**
> ...i find debian faster and more stable...

than Ubuntu?  Also, etch or lenny?

---

### Post by kerry_s on 2007-10-04
> **ArtF10 said:**
> I've been using XFCE in Zenwalk and it is lightning fast but I've always wanted Gnome to run faster and after  googling, reading and following "10 ways to make Ubuntu faster" I seem to understand that swap would be faster?  Anyways, I guess I'll just have to live with what I have since a custom install went ballistic on me.



than Ubuntu?  Also, etch or lenny?

yes, faster than ubuntu.
gnome is just not built for speed, it's made to function like xp, so in the long term it gets slower.

all of the above, mines upgraded all the way up to sid. don't recommend if you want stable. etch/lenny is perfect for the average user, just install etch and add the lenny repo's.

---

### Post by __knk__ on 2007-10-04
all sounds promising i still want to try elive, i had to get the stable version off a torrent however which was a little ridiculous considering they advertise themselves as being free yet do not let u download without a "donation" the development versions are available off the site however.  i might resize my larger partition and leave around 10gig at the end of it for elive and see how i go.  looks very promising considering minimum specs are 100mhz:)

---

### Post by LuisC-SM on 2007-10-07
@kerry_s
Can you please tell me your system specs?
Ubuntu x.xx or debian ?
and what window manager are u using?

Thanks in advance

Luis

---

