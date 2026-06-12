---
title: "Installer freezes and weird screen appears"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by mattmac24 on 2006-08-25
just a note that may be relevent, i burned the cd image to dvd as i didnt have any blank cds available. when i insert the cd the normal menu came up and i went to "verify cd" (or similiar name) and it passed.

My problem is that when i try to install ubuntu i get past the partition setting up, past the network config, and then it installs the base package(well tries to). Somwhere in this process of actually installing ubuntu the screen goes completly black, except for two small white rectangles.

This ma be kind of hard to picture but my screen is completly black with a 1.5cm by .5cm whie box about 5cm down from the top left corner and 1cm in from the edge of the screen.

the same box is also present i the same way except that it is about 15cm in from the left side of the screen.

Ive tried leaving it on all night to see if anything happens as well as redoing the whole thing about 4 times. When i woke up after leaving it on all night the screen was the same, but the cd had been ejected.(dunno wat that means)

Im desktop is a P4 2.4Ghz computer with the 845 chipset(just looked it up on the intel site). im using the onboard eveything

not sure if this piece of info will help but the same comp can boo the kubuntu live cd just fine.

Thanks for your help,


Matt

---

### Post by mattmac24 on 2006-08-26
Hey, im sure there are heaps of people who know wat is going on here and how 2 fix...or at least a way of telling what exactly is killing my install. any ideas at all would be great.

Matt:)

---

### Post by randell6564 on 2006-08-27
Hi! Well, if it were me, i would get a hold of a cdr and burn another iso first. You know, could be a DVD thing! 

What kind of "onboard" graphics hardware do you have?

---

### Post by mattmac24 on 2006-08-27
um.....how do i tell, its not like a extra card i went out and bought so im not realli sure bout that.

and abo burning to cds...i do need 2 get some but dont have any atm...could this actully make a diffrence?

thx

matt

---

### Post by randell6564 on 2006-08-27
> **mattmac24 said:**
> um.....how do i tell, its not like a extra card i went out and bought so im not realli sure bout that.

and abo burning to cds...i do need 2 get some but dont have any atm...could this actully make a diffrence?

thx

matt

It's made a difference for me in the past.  I went out a while back and found Suse 9.3 at 'Best Buy'.  I was pretty excited to see a Linux distrobution in a store, so I bought it.  It came with books, two DVD's and 5 Cd's! 

I never had problems installing with the cd's, but never could get it using the DVD's.  Dont know why, but thats what happened.

As for finding out what's on your board, I know that there is a command that you can type at the terminal that will list your hardware, but it escapes me at the moment. (maybe 'dmesg')

Or look in your menu for something related to hardware.

---

### Post by knuttz on 2006-08-27
I'm having the same problem, and I did burn the iso with a CDR.
I think it might be a graphics problem, but not sure what to do about it.

---

### Post by randell6564 on 2006-08-27
> **knuttz said:**
> I'm having the same problem, and I did burn the iso with a CDR.
I think it might be a graphics problem, but not sure what to do about it.

HI!  Might be helpful if you and mattmac could compare hardware.

There is plenty of folks here that can tell you what to type at the terminal to get a list of your hardware.

---

### Post by mattmac24 on 2006-08-27
ok found that if i just leave it on for a while the cd ejects...then it will automatically restart the comp a while after this, when it restarts it tries 2 load grub but gives an error, but if u boot the cd and then choose boot from frist hard disk, ull get straight into ubutu perfectly. but im just not sure if this will muck up the install as some of the installation setting where not set(not sure what there is left to do after it installs the files.

Matt

---

### Post by randell6564 on 2006-08-27
> **mattmac24 said:**
> ok found that if i just leave it on for a while the cd ejects...then it will automatically restart the comp a while after this, when it restarts it tries 2 load grub but gives an error, but if u boot the cd and then choose boot from frist hard disk, ull get straight into ubutu perfectly. but im just not sure if this will muck up the install as some of the installation setting where not set(not sure what there is left to do after it installs the files.

Matt

OK, I'm familiar with this issue.  I had this same problem when i was trying to dual boot, except I was getting 'Error loading operating system'

Go into your Bios and set it to LBA. It's default will probably be 'Auto'
Save the setting and try and reboot without the cd.

---

### Post by mattmac24 on 2006-08-27
> **randell6564 said:**
> OK, I'm familiar with this issue.  I had this same problem when i was trying to dual boot, except I was getting 'Error loading operating system'

Go into your Bios and set it to LBA. It's default will probably be 'Auto'
Save the setting and try and reboot without the cd.

i cant seem to find this option in my bios. Ive gone through and checked every option. if it helps my BIOS version is R84510A/86A.0033.P16.

and to the guy with the same problem, you wouldnt be using the intel desktop board D85GEBV2 would you? im using the default video card that comes onboard with that mothor board.

thanks,

Matt

---

### Post by randell6564 on 2006-08-27
> **mattmac24 said:**
> i cant seem to find this option in my bios. Ive gone through and checked every option. if it helps my BIOS version is R84510A/86A.0033.P16.

and to the guy with the same problem, you wouldnt be using the intel desktop board D85GEBV2 would you? im using the default video card that comes onboard with that mothor board.

thanks,

Matt

Strange. Nothing that reads CHS,LBA, Auto?
Well if you can find something like that, it fixed my booting problem.
I could be wrong, but it worked for me when I needed to boot with the cd and select 'boot from first hardisk'

---

