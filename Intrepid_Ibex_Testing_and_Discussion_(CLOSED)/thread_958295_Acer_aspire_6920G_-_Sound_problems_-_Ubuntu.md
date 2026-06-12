---
title: "Acer aspire 6920G - Sound problems - Ubuntu"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by RadicalRaid on 2008-10-25
I had the same problem with an Acer 6920g and after a night of heavy googling, I found that the linuxant driver ( [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) ) made all my problems go away! Everything worked fine and I could even use my bluetooth headset ( which had been a drag getting to work before ).

I haven't tried the latest version there yet, since I don't need to fix what isn't broken. But I'm pretty sure it will work fine.

Hope this helpes someone!

Edit: I'm using the 8.10 entriped beta version, which may be relevant.

---

### Post by RadicalRaid on 2008-10-25
I had the same problem with an Acer 6920g and after a night of heavy googling, I found that the linuxant driver ( [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) ) made all my problems go away! Everything worked fine and I could even use my bluetooth headset ( which had been a drag getting to work before ).

I haven't tried the latest version there yet, since I don't need to fix what isn't broken. But I'm pretty sure it will work fine

I'm using the ubuntu intrepid version, 8.10 beta.

Hope this helps someone!

---

### Post by RadicalRaid on 2008-10-25
I had the same problem with an Acer 6920g and after a night of heavy googling, I found that the linuxant driver ( [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) ) made all my problems go away! Everything worked fine and I could even use my bluetooth headset ( which had been a drag getting to work before ).

I haven't tried the latest version there yet, since I don't need to fix what isn't broken. But I'm pretty sure it will work fine

I'm using the ubuntu intrepid version, 8.10 beta, but I'm pretty sure it'll work in 8.04.

Hope this helps someone!

---

### Post by RadicalRaid on 2008-10-25
I had the same problem with an Acer 6920g and after a night of heavy googling, I found that the linuxant driver ( [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) ) made all my problems go away! Everything worked fine and I could even use my bluetooth headset ( which had been a drag getting to work before ).

I haven't tried the latest version there yet, since I don't need to fix what isn't broken. But I'm pretty sure it will work fine

I'm using the ubuntu intrepid version, 8.10 beta, but I'm pretty sure it'll work in 8.04.

Hope this helps someone!

---

### Post by RadicalRaid on 2008-10-25
I had the same problem with an Acer 6920g and after a night of heavy googling, I found that the linuxant driver ( [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) ) made all my problems go away! Everything worked fine and I could even use my bluetooth headset ( which had been a drag getting to work before ).

I haven't tried the latest version there yet, since I don't need to fix what isn't broken. But I'm pretty sure it will work fine

I'm using the ubuntu intrepid version, 8.10 beta.

Hope this helps!

---

### Post by overdrank on 2008-10-25
> **RadicalRaid said:**
> I had the same problem with an Acer 6920g and after a night of heavy googling, I found that the linuxant driver ( [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) ) made all my problems go away! Everything worked fine and I could even use my bluetooth headset ( which had been a drag getting to work before ).

I haven't tried the latest version there yet, since I don't need to fix what isn't broken. But I'm pretty sure it will work fine.

Hope this helpes someone!

Edit: I'm using the 8.10 entriped beta version, which may be relevant.

Hi and welcome, I have merged all of you posts into its own thread and moved to the  Intrepid Ibex Testing and Discussion
:)

---

### Post by dream_coder on 2008-10-25
Doesnt work on Acer 6920G with intrepid x64 sound refuses to work!

---

### Post by zorkerz on 2008-10-25
Many peoples sound is unexplainably getting muted in alsamixer. To check this open a terminal and type 'alsamixer -Dhw' then check that your PCM sound is turned up. Check out this post too [http://ubuntuforums.org/showthread.php?t=942529&highlight=sound](http://ubuntuforums.org/showthread.php?t=942529&highlight=sound)

---

### Post by dream_coder on 2008-10-26
My sound isn't muted, but still no sound, I have gone back to windows anyhow, can someone please post when there is a fix and I can swiftly move back to Ubuntu, thanks this would be greatly appreciated.

---

### Post by zorkerz on 2008-10-26
Im sorry dream coder that you have had trouble with your sound. I do not know in particular what is wrong for your sound so will not know when a fix occurs. Its good to be able to go back to windows It seems you took the dual boot root. I hope you do not give up on linux after only trying a beta release. Beta's exist so that they can be tested and improved they are expected to have bugs. If you felt like helping I would recomend filing a bug at launchpad to do that maybe here is a good place to start. [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

if you can give more specificts to your problem it becomes easire to tell what is going wrong.

good luck

---

### Post by dream_coder on 2008-10-26
I have been Ubuntu only for around year and a half now, I managed to get sound working through a couple of speakers on hardy using the workaround using hda-verb on my acer 6920G, I still have Ubuntu only on my home PC, and to be honest I cant stand windows lol, but with my laptop it has 5.1 surround sound, and a bluray player, and making bluray play in Ubuntu is tedious and not guarenteed to say the least, using 8.10 for a few days and tinkering about I have to say if the sound was working I would have definately stuck to it, it has lots of improvements over hardy including not having to type the SSID and also password everytime I want to connect to my home wireless network.

I will just keep checking the progress of other peoples posts on here until a fix or update or workaround is found.

Cheers

---

### Post by RadicalRaid on 2008-10-26
Too bad it's not working on the 64 bit version.
My guess is that it will work on the 8920g tho ( 32 bit, offcourse ).

I'm not sure for which soundcards it'll work, or why it works PERIOD. But it helped me a lot.

If anyone uses the antlinux driver, be sure to check for updates every now and then. Especially after the update-managers made his rounds because it may disable the driver. Simply reinstall the version that worked for you.

The link again: [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

---

### Post by dream_coder on 2008-10-29
Found a Solution!

if you edit/reduce asla-base to jus this -

options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto 

Then Reboot!

Sound works althought subwoofer does not maybe changing model to acer-aspire?

3 People have tried the solution with model=auto with Success :)

---

### Post by schlady on 2008-10-29
Hi,

i just installed the linuxant alsa deb-package on my x86_64 Intrepid system (yes, its 64bit!) and it works perfectly WITH subwoofer. to turn the subwoofer on i had to set the headphone switch in gnome-volume-control.


my module option is now:
options snd-hda-intel model=acer-aspire

and i use the hda-verb fix from [http://jan.saell.org/blog/archives/30]("http://jan.saell.org/blog/archives/30") at bootup.


schlady

---

### Post by dream_coder on 2008-10-29
The option model=acer-aspire does not work for me but model=auto works flawlessy with subwoofer as previous post, and I am not using hda-verb so not sure if that is needed at all.

---

### Post by dream_coder on 2008-10-29
The option model=acer-aspire does not work for me but model=auto works flawlessy with subwoofer through gnome-panel as previous post, regarding hda-verb I do not have it installed and works fine so not sure if that is needed at all.

PS Wasn't I the one who suggested you try that solution in #ubuntu+1 ? lol

If so good work! :)

---

### Post by schlady on 2008-10-29
dream_coder, yes you were the one.
Thanks for your hints!

I just tried model=auto again with and without the hda-verb fix - sound worked but without subwoofer in both cases.

And if I use model=acer-aspire, subwoofer only works if I apply the hda-verb fix!

Maybe acer used different revisions of the alc889 codec in our 6920G?!


schlady

---

