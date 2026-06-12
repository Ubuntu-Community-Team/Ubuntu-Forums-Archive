---
title: "iPhone and Lucid"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Atermoon on 2010-03-07
I've seen many people talk and blog about Lucid and iPhone support out of the box but it seems it's only working for some. My girlfriend has an iPhone with the latest 3.1.3 firmware and I just can't find a way to transfer any music to it. It mounts automatically when plugged and I can browse the files with Nautilus and I see it in Rhythmbox but that's it.

When I try to transfer a song with Rhythmbox it shows the progressbar and after that I can play the music from Rhythmbox but it doesn't appear in the iPhone itself. Also after I unplug it and plug it back the new songs don't even appear in Rhythmbox.

Anyone with better luck please let me know how to transfer music to the damn thing :P

---

### Post by Rob2687 on 2010-03-07
It's rather buggy right now. The exact same behaviour has happened over here. Also when I tried to sync again on Itunes it decided to resync the entire music library again. Only a couple of times has it been able to successfully add music to my iPod Touch. In addition I've found that creating folders or transfering/modifying folders on on a jailbroken iPod Touch doesn't work right. 

All of these problems indicate an incomplete implementation of iPhone support. The sync problems are most likely because iTunes expects complete and exclusive control over the device. So as soon as it notices something it doesn't like it goes into panic mode and decides to wipe and restore. Plus coding the Linux support is pretty much backward engineering whatever protocols Apple cooked up to sync the device which can't be easy.

---

### Post by Atermoon on 2010-03-07
I get that it's not easy at all to implement and I'm not complaining because it's not working or anything like that. I'm just wondering how some people managed to get it working.

---

### Post by Atermoon on 2010-03-08
Ok, I finally got it to work. Took me a bunch of hours of trying all kind of stuff and seems like what fixed it was creating a playlist in the iPhone from Rhythmbox. I have no idea how and why but after that I was able to add songs that did not disappear after unplugging the iPhone.

The one thing I can recommend is to keep the iPhone connected for a few seconds after Rhythmbox finishes copying the songs. You'll see a "Synchronizing.. bla bla" message on the phone - wait for it to disappear.

p.s. it's a 16gb iPhone 3G with 3.1.3 firmware and no jailbreak.

---

### Post by cyberkilla on 2010-03-08
Seems to work for a lot of people, and having spoken to some of the people behind it, they are adamant that they've made great progress.

Still, I'm holding off using it for the time being. The damned thing is broken enough without subjecting it to linux**.

**Can't download podcasts or music through the iPod iTunes store. It only works if I download the podcast on the computer and sync it over...

---

### Post by xlash on 2010-03-10
Can you share some light on your findings?

On my side, Rhythmbox and Nautilus shows the Iphone, I can read from it, I can transfer to it (displays a progress bar), but it never syncs. 

As soon as I disconnect it, it's gone.

My iphone never displays a Sync message, have you always seen that from Rhythmbox?

Thanks

---

### Post by nwadams on 2010-03-10
hi. i'm very impressed with the progress so far. 
For me when i transfer music over with rhythm box it copies over to the Ipod. Next time I plug my ipod in, rhythm box detects the music. But my iPod doesn't detect the music so i cannot play it. Any ideas??

I have a 16 gb second gen ipod touch

thanks

nwadams

---

### Post by xlash on 2010-03-10
After adding the HashInfo and SysInfoExtended (see here : [http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/)), synchronization works for me!!!!!

Except for playlists!
Actually, playlists are added, saved correctly, but I cannot successfully add songs to it, nor view/use them on the iPhone iPod software.

---

### Post by NRK on 2010-03-11
> **xlash said:**
> After adding the HashInfo and SysInfoExtended (see here : [http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/)), synchronization works for me!!!!!
Except for playlists!

It worked for me too! Maybe at this time that part (HashInfo and SysInfoExtended) is not automatic yet, I HOPE it'll be soon :)

---

### Post by goodrench on 2010-03-27
> **cyberkilla said:**
> Seems to work for a lot of people, and having spoken to some of the people behind it, they are adamant that they've made great progress.

Still, I'm holding off using it for the time being. The damned thing is broken enough without subjecting it to linux**.

**Can't download podcasts or music through the iPod iTunes store. It only works if I download the podcast on the computer and sync it over...

Try RSSPlayer. It will download podcasts directly onto the device. No need for pc.
Great app. Worth the $$$.

Also I had problems with playlists, but unmounting and rebooting the device seemed to do the trick.

---

### Post by FunkyM on 2010-04-01
> **Atermoon said:**
> ... When I try to transfer a song with Rhythmbox it shows the progressbar and after that I can play the music from Rhythmbox but it doesn't appear in the iPhone itself.

Your issue is related to one a lot of people seem to have.

You have to wait for Rhythmbox to actually sync the music database onto your device!

This happens by showing the "Sync in Progress..." screen on your device. If you unplug the device before that step, nothing will change on your device.

Since Rhythmbox appears to do that sync step rather "sporadically" people do not understand they must wait for it.

This is being worked on for future releases to directly sync after all tracks are copied like iTunes does.

If this is not your issue, it would help if people would report bugs in the official bugtracker at [http://libiphone.lighthouseapp.com/](http://libiphone.lighthouseapp.com/)

---

