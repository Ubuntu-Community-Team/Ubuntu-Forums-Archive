---
title: "Migrating from one drive to another..."
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by Schrodinger's Hamster on 2006-11-17
Hi all;
 
I have found references to what I need to do on this forum, but none relate exactly my situation so I am a bit hesitent to use them given my lack of linux experience...
 
I installed Edgy on my laptop after shrinking the XP partition to make room for it (50gb) and set about learning linux. During my learning I managed to kill Edgy so badly that I decided to reinstall, but rather than write over my existing Edgy partition (which I had some hopes I might be able to rescue) I pulled the SATA drive and used a spare 60gb one I had.
 
Now, my new install has taken me a few weeks to sort out but it is now working exactly as I want it to; I am more or less confident I could reinstall on my main drive and acheive the same thing, but if there was an easy way for me to take the installation that works and paste it over the top of the one that doesnt on the other drive it would save me a lot of time :)
 
I cant fit both drives at the same time and I dont have any way to mount one externally, but I do have a built in DVD writer so it seems to me that I should be able to create an image and just write it to the other drive / partition after I refit it - probably using the live CD?
 
If I do this (and any pointers on what commands / packages are appropriate would be appreciated) would the bootloader care that the installation is not the one that created it or that it was originally pointing at? It would be on the same partition the Ubuntu option on grub was pointing at, but would it load the same?

Thanks for reading, and for any suggestions :)

---

### Post by dogon on 2006-11-17
My suggestion would be... Don't even try it... :???: 

Its possible to do a direct copy from drive to drive. But as you said your bootloader might object, and I believe (not sure) the kernel was also a bit specific about where you put it. Also there is technically other hardware in your system. So this too could cause problems too.

I am guessing you installed software and configured everything to be cool and what you really want to accomplish is not having to do it again.

I'd suggest opening your favourite text editor and make a list of the programs you wish to keep. Then backup your home directories, and your etc directory. If you use services like apache or mysql, make sure you copy their data folders aswell.

Install ubuntu on the target drive. And all the packages you wish to use. Replace your home dir with your backup Home dir. This should restore the settings for most of your apps. And for any services like apache you can use the backed up etc dir and the data folders to restore whatever you had in there.

The method is a bit more labour intensive, but its simple I transferred my system this way in under 4 hours. 

One warning, I never really managed to copy evolutions data folders. Since I didnt use it much I never bothered to research it either.

---

