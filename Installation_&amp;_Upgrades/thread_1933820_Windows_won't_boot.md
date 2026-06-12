---
title: "Windows won't boot"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by DonutFUN on 2012-03-01
So I'll start from the beginning:
For about 3 months I have been running Windows XP without any issue since my last format, I haven't had any trouble with that at all.
I decided since I saw how much Ubuntu had updated since the last time I had tried it I would run Wubi and see if it would finally support my video card, I was ecstatic when I had finally gotten Wubi all set up and updated to find out that it did! 
So from there I put another hard drive (120Gb) into my computer (and unplugged the other ones as to not risk writing over them) and installed the latest Ubuntu 11.10, updated it, got it all working, and then plugged in my other hard drives again (a 1.5Tb full of just media and backups, and my 500Gb Windows) I mount the media drive to see if I can start listening to music, and set up a custom desktop wallpaper and all of that fun stuff, and it was all working great.
Since then I had installed Wine, just for fun, to test it,, I mounted my windows Hdd and ran a couple programs and it was working great still.
Then I tried this morning to boot into windows, what I did is when my computer boots I can hold Esc to load a boot popup menu and it lets me choose the drive to boot from, so I chose the one with windows on it, the boot menu showed up saying "Windows XP" and "Windows XP Recovery" or something like that (Compaq recovery partition by the way), and I let it time out and chose windows, and all it did was restart, back to the boot diagnostic screen, so I went into the bios and changed the whole boot order there to have the windows disk first, still nothing, I actually got to the point where I unplugged my Ubuntu drive and still nothing!
The reason I installed them on two separate drives independently was so that they would NOT mess with each other AT ALL! but apparently they did.
I know that I can just reinstall Windows again, its not a huge deal, but I want to know WHAT went wrong, why it happened, and if it will just happen again.
And how to fix it if possible?
I know there was still a good Boot.ini (I believe I have messed it up since) and I even tried the Windows CD and it doesn't even detect that Windows is installed on any of the drives.

---

### Post by oldfred on 2012-03-02
If you booted into the recovery partition it often starts the recovery process. It may have overwritten MBR or partition table with the defaults as it was when purchased.

Post link to  boot info script.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

