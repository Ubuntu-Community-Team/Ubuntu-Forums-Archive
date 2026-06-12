---
title: "NOOB: few problems"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by paulb100 on 2008-11-08
hi all

Im a Linux noob and have managed to install ubuntu and dual-boot wit Vista
after some teething problems with Audio I managed to get it running perfectly (so far)

however,

during install I didnt have a partition ready for a swap-file as I wasnt told that I would need one>?  will I have to install it on a partition? can I do this without re-installing it? my ubuntu is installed on a 10Gb partition and uses 3Gb , it seems to be working fine...

also:

1. is there a webmail client that will retrieve my hotmail emails?
2. should I install an Anti-Virus?
3. how do I get programs to run at log-on?
4. is there a way to get it to stop asking for this key-cycle password which seems to enable my wifi..?
5. which is the best web-design program for linux?

thanks

---

### Post by Chunky Dunk on 2008-11-08
The swap would need its own partition, but if you have a bunch of memory, you could probably get by without one. Or you could make a swap *file*
This will give some info... [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

as for question #2, you don't really need an anti virus program for linux, since linux doesn't have a virus problem like windows does.

Question 3: Go to "System" >> "Preferences" >> "Sessions" and you can control what starts when you log in.

---

### Post by tvtech on 2008-11-08
as far as web design goes there are a couple wysiwyg programs out there. if your just interested in coding I'd say [[COLOR="Blue"]bluefish[/COLOR]]("http://bluefish.openoffice.nl/") is by far the best.  I've never been much of a wysiwyg person myself.  check out the available apps in the repositories. via add/remove software.  if that doesn't float your boat check out [sourceforge]("http://sourceforge.net/")

I've used kompozer before it's okay.  I like dreamweaver as far as wysiwyg's go but it doesn't run on linux.

---

### Post by paulb100 on 2008-11-09
thanks for replys - unfortunately i tried sessions but found that I dont know what to enter in the boxes that pop up???

also regarding swap - I have 2Gb of RAM and dual-core - it seems to run perfectly and it says in that link that a partition ISNT required for a swap file - a swap file can be on the same partition as the OS and its just the same effectively.... how do i know if I have one running or not? - all it said at install was "which partition do i want to install swap on?" or summit like that anyway

can anyone help with this?

I want pidgin to run and a mail client that will retrieve HOTMAIL emails...

thanks

---

### Post by andrew.46 on 2008-11-27
Hi,

I have taken the liberty of only answering those of your questions that I know about :-)

> 2. should I install an Anti-Virus?

bodhi.zazen has written security overview for new users of Ubuntu: [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812"). I would strongly recommend that you have a read.

> 5. which is the best web-design program for linux?

Well I cannot say which is the *best*, but I have had long experience with Bluefish and I believe it is certainly one of the better offerings:

```
sudo apt-get install bluefish
```

All the very best,

  Andrew

---

