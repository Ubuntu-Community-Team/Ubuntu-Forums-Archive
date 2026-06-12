---
title: "A few install problems"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by bsh on 2007-09-04
Right, i'm new to linux, so this may be a stupid/useless thread, but at least i give some feedback (maybe this isn't the right place to do, but anyway...)
One thing i must emphasize, i do not have internet connection at home! Keep that in mind.
So i installed ubuntu 6.10 x86 desktop to my secondary pc. boot up with the live cd, everything was ok, then clicked install. however, at the step to select the system time and timezone, it displayed wrong time (2 hours ahead of the bios clock). I tried setting the time, but it kept hanging here. The clock counted but the installer stopped responding. Killed it and tried a few times, same happened. Is that a bug?
So i continued the install without adjusting the time, all went fine.
Then i decided to remove this 6.10 and install a 7.04. I booted from the live cd, but unfortunatelly i forgot to set the language to hungarian and booted in english. No probs, i knew i can set this later in the installer. It still displayed wrong time, and i didn't even have the option to adjust it, so left it as is. at the partition part of the install, i have had problems. i wanted to format the existing ext3 partition and mount it as /, but it only allowed me to format and i couldn't change the mounting point (it wanted to mount it in /media/hda1 blahblah) (i have an ntfs partiton and a linux swap partition too). the installer won't continue coz i haven't defined the root partition (bacuse i can't) so i ended up removing the two linux partitions and create new ones, so i could set the mounting point. is this a bug?
after that, at some point (83% or so), it told me it "downloads language packs", but it did nothing, since i have no internet connection. i wondered why's that, since 6.10 installed the languages from the cd as far as i remember. so i skipped this and finished installing.
on the next reboot it did some disk error scanning and found one error: last disk maintenance time was set in the "future". i guess it's because the installer used wrong time? it corrected it and worked fine.
but, it ended up with a mixed language interface. login screen was english, i selected hungarian to no avail, the desktop was english in parts and hungarian in other parts. when i tried to run a terminal, it displayed many weird characters, i guess some wrong character map was used due to the half-english-half-hungarian setting.
any way i can correct this without a working internet connection?
and just a side not: i find this very annoying, if one has no internet, installing ANYTHING is nearly impossible due to many dependencies etc. i tried installing the nvidia driver, even that wanted to download things! annoying that is.

---

### Post by banewman on 2007-09-04
You should be able to sort out the language issue with your cd. It should load from your install cd but if it won't you will have to go to the synaptic menu bar and select settings - repositories and add your cd, best to check this before doing anything else.Put it in the drive then open synaptic     - system-synaptic package manager - in the menu, then click on search and type "language-pack". Click the ones that are selected and choose to completely remove them to get rid of the errors, then select the one language you want. Hope this helps.

---

### Post by bsh on 2007-09-04
thanks will give it a try when i get home.
btw i remember i tried installing languages and there was only english and hungarian, both were installed/selected so i couldn't do much, it still doesn't work. will try this synaptic thing (but i think that's the same as i alredy tried)

---

