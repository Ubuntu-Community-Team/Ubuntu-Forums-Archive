---
title: "Problems with the new Usplash?"
date: 2008-05-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2008-05-29
I'm getting some alarming things during boot/reboot---upon reboot the system will emit large numbers of bios warning beeps & goto text display. Startup is just as dicey--bios warnings at several points in boot with text only display. This is with a Gigabyte motherboard that will boot without problems in Hardy.

Has anyone see this problem?  If so, I've started a bug report at  [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662)


Any ideas anyone?

---

### Post by autocrosser on 2008-05-29
OK--I've pinned it down---I run my menu.lst with "splash" not "quiet splash" so I can watch the boot progress--as soon as I changed the kernel line back to "quiet splash", the problem went away. Looks like a regression to me.

---

### Post by ronacc on 2008-05-29
I too run with "splash" and not "quiet splash" my mobo is a gigabyte GA-M55plus-S3G . I have not seen this yet .my usplash version is 0.5.21 and usplash theme is 0.18    . I am 64bit .

---

### Post by autocrosser on 2008-05-29
Interesting--I'm running 32bit & a GA-P35-DS3L (rev2).  I was running a custom splash when this first started & changed back to the stock one--still had the problem til I ran "quiet" (don't like quiet :(  ).  I'll wait til one of the devs contact me--I would say that it won't take long (usplash is a pet project anyway :)  ).   How is 64 treating you?[COLOR=#FD6724][/COLOR][COLOR=#FD6724] 




[/COLOR]

---

### Post by ronacc on 2008-05-29
no serious problems yet , theres not all that much of Intrepid out yet . I expect the fun to begin about the time of alpha 1 . I'm still on the hardy kernal , I wait for the "official" kernel rather than build my own .

---

### Post by autocrosser on 2008-05-29
Yes--I try to stay with all (within reason) "stock" repos--So I wait for the Nvidia driver,etc,etc.....

I've been toying with running a 64bit partition--fresh Hardy & Ibex-it---might play with it this weekend....

---

### Post by ronacc on 2008-05-30
yes during the developement cycle I (mostly) stick with the packages from the repos also, after all thats what we are supposed to be testing . I do however install the latest Nvidia beta driver. The Ubuntu version is non functional too much of the time and I get tired of low graphics mode nuking my destop :lolflag:

---

