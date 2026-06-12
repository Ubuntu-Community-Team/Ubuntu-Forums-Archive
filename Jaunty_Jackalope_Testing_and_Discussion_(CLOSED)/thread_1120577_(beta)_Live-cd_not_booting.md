---
title: "(beta) Live-cd not booting"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by priegog on 2009-04-09
Hi, so here's the deal. I downloaded the beta live-cd a couple of days ago to install on both my computers. I am running it on one of them, so that went fine, but the other one refuses to boot off of it. It's an old Motion Computing M1300. It doesn't have an optical drive, so naturally I try to boot it with a usb dvd burner. I've since tried the daily images to no avail. The alternate cd refuses to go past the first menu screen also (the same thing that happens to the live cd) It doesn't give me any error message so I have no idea what's going on. After I select "try ubuntu without making any changes to your computer" the screen just goes black and stays that way.
Since then I've also re-downloaded the intrepid live cd to make sure the drive or the computer weren't broken, and it does boot off of the intrepid live cd.
So... Any ideas guys?

---

### Post by ronacc on 2009-04-09
when the menu comes up hit e (to edit) and remove "quiet" from the kernel line so you can see what is happening .

---

### Post by priegog on 2009-04-09
Ok, here's what shows in the screen when it stops working (sorry for the picture, I'm oo lazy to type it all):

---

### Post by ronacc on 2009-04-09
try this , where you removed "quite" put in "noacpi"   (without the quotes)

---

### Post by priegog on 2009-04-09
thanks a bunch! That seems to have done it. Any idea why 9.04 would need this parameter while 8.10 doesn't? What has changed?

---

### Post by ronacc on 2009-04-09
a bunch has changed as always with new versions , I have no idea which particular one has caused the problem , I just know that noacpi sometimes is need to get some particular systems to boot , and also nolapic is sometimes needed . its an easy thing to try when a boot on a new version stalls . once you install the system add that to the bootline in /boot/grub/menu.lst   .

---

### Post by priegog on 2009-04-09
Yeah, that was the next thing I was going to ask you, how to add those functions once installed. Thanks a lot. Altho I think you meant remove those from the line, since it's harsh to live without acpi events, and I KNOW the kernel should support it, unless it's some sort of regression... Anyways, Thanks!

---

### Post by priegog on 2009-04-18
Humm... removing the "acpi=off" line in the installed version won't let me boot. Now I'm sure this is some sort of regression. I know it won't get fixed in time for the release, but nevertheless, how on earth should I file a bug like this? I've searched in launchpad and there don't seem to be any bugs about this. For instance when I submit a bug I have to say what package/application is the bug related to. So what package is THIS particular bug related to? The kernel itself? I've read the bug submitting guidelines, but AFAIremember it doesn't say how to submit this inespecifical kind of bug. 
help, please?

---

### Post by ronacc on 2009-04-18
you don't have to specify a package , just use "I don't know" and who ever triages it will determine the package . also did you just remove "acpi=off" or did you add "noacpi" ?

---

### Post by priegog on 2009-04-18
Oh, thanks.
Uhmmm I'm pretty sure I removed acpi=off, since I wanted those functions. I can't check now, because I downgraded to intrepid. I'll have to mess with it again to file the bug tho. What's the difference between the 2?

---

### Post by ronacc on 2009-04-18
I'm not sure of the differecne between the 2 , possibly when in the boot process the take effect .

---

