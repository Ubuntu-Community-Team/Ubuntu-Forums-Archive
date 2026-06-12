---
title: "Itching to jump in.. HELP"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by KatieCook on 2007-02-15
Ok, I am soo ready to put ubuntu on my xp machine. Tired of playing with the Live CD and want to install, and want to keep windows intact BUT...

  I have: 

  AMD 64 Processor 3500+
  1 G RAM
  C) 180 Gb - 163 Gb free
  D) 4 Gb - 2 Gb free

  Windows XP MCE SP2


  My question is ..  How do you partition again when you already have one?
I only want windows to have 63 Gb and want to make Linux have 100 Gb can I do that?

---

### Post by veloce on 2007-02-15
Just do it!

The install procedure steps you through this.  I believe you'll get to choose which partition to shrink and by how much.  

And don't forget the standard advice before you start:
[LIST=1]
[*]defragment your disk
[*]backup up anything you just can't lose.
[/LIST]

I bit the bullet and did a complete reinstallation - windoze is no more.  I use vmware server to run windows occassionally for anything that just has to be done that way.

---

### Post by kdub432 on 2007-02-15
well, from what i gathered, windows is still installed on your hard drive. 

Get a program similiar to PartionMagic for windows. (Its commercial, but really good. If you want to take the freebie route, look into a gparted livecd...) Install it, and you can use it to resize and move your partitions around, without destroying data. Resize the windows partition to 63 gigs and leave 100 gigabytes for linux. Then you can pop in your livecd, and hit install. You'll want to use its partitioning utility to set aside about 1gig for linux swap space (linux's virtual memory) and the remaining 99 for your root drive. Dont touch your windows partition while installing ubuntu though. It'll install, and when you reboot, you'll have a choice as to whether you want ubuntu or windows to boot. 

Post back with problems.

---

### Post by KatieCook on 2007-02-15
> **veloce said:**
> Just do it!

The install procedure steps you through this.  I believe you'll get to choose which partition to shrink and by how much.  

And don't forget the standard advice before you start:
[LIST=1]
[*]defragment your disk
[*]backup up anything you just can't lose.
[/LIST]

I bit the bullet and did a complete reinstallation - windoze is no more.  I use vmware server to run windows occassionally for anything that just has to be done that way.

You just have NO IDEA how tempted I am to just do it.. I could save my files or put them on my other computer and then get them back but.. I have a few programs that WILL NOT RUN on linux and I can not part with them :)   

Oh yeah and Yahoo messenger for the voice (online meeting every week)


One is Overdrive.. (for listening to my audio books through supscription) and the other is Itunes for my IPOD which without Itunes I am very very very limited in the use of my IPOD.. Honestly the files are the least of my worries.. LOL 

But.. If those other programs will work with linux I am there!!!  And believe me when I say I would not even look back!

---

### Post by veloce on 2007-02-15
Well, as I said, I use vmware server for the few things that have to have ms windows. If I were you, I'd search the forums for people using your "must keep" software and vmware.  May be the HOWTO has already been written...

---

### Post by JensenDied on 2007-02-15
I'm not familiar with overdrive, but I have found that gtkpod for Linux (or windows with cygwin, but thats a bitch in itself to get working there) works for syncing ipods. to or from your music library.

It will automatically convert your music to the type that the iPod uses much like iTunes does when you initally add to its music library, however I have noticed that with certain audio files (.MP4 's  in my experience) will not convert if you don't have the correct audio library/codec for the transcoding of the file.  (this may have been about 2 albums worth of songs over the last 3 iPod's ive synced for people (iTunes isn't friendly with other iPods from what I hear).

you should be able to find it in the universe repoitories

---

