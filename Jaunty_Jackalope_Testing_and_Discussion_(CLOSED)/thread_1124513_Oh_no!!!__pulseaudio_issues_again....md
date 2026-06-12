---
title: "Oh no!!!  pulseaudio issues again..."
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by viduliya on 2009-04-13
Most of last summer I was trying to overcome the constant set of issues introduced by the inclusion of pulseaudio to Hardy.  The Intrepid release seem to have most of these problems ironed out.  Now again, in Janty beta pulseaudio is causing a lot of headache.  I am writing as I am rebuilding a machine which I effectively messed up trying to get pulseaudio kind of working.

My problems on three different machines with pulseaudio:

[LIST]
[*]Choppy sound in applications like Rythmbox
[*]Choppy flash and audio,video sync problems in flash videos
[*]Insane amount of messages in /var/log/user.log
[*]Insane CPU usage slowing down the machine specially when using Skype
[*]Sound kicks out for no reason while using Skype and hangs forcing me to kill Skype or reboot if the whole system has hung.
[/LIST]

I thought my laptop was on fire after using skype for 1/2 hour.  There is no reason I can think of to having pulseaudio if it chews up that much CPU.  

Dare I say that Ubuntu behaves worse than VISTA with pulseaudio.  I really want the new versions of software with the stability we had with sound in Feisty and Gutsy.  I really did give it a shot but now, I do not think pulseaudio is ready for prime-time use.  Constant pulseaudio problems are ruining my Ubuntu experience.  There has to be a better alternative to putting up with these pulseaudio problems.  I have used many Linux distributions for many years the last distribution (Gentoo) was quite good for a long time until the packages started to be very buggy and I was spending more time fixing problems on my machines than using them.  I really like Ubuntu and I hope Ubuntu is not going the way of Gentoo.  Can some one please suggest a viable and functional alternative to using pulseaudio and how I may disable pulseaudio for good to continue using Janty to save my sanity.

Thank you.

UPDATE:
Only possible way to use Ubuntu Janty release normally with popular audio applications is to keep the pulseaudio monster at bay by making sure it is disabled and using alsa.  Following the instructions on [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/").  

Sad thing is that under Intrepid pulseaudio seemed more functional.  Under this Janty release which is suppose to be a LTS release, audio is unusable with too many issues.  Following the instructions in the above link to disable pulseaudio and use alsa makes all audio issues disappear and all audio applications just work!  Maybe I will try give another shot at using pulse audio in October when Ubuntu 9.10 is released until then alsa is good for me.

---

### Post by amano on 2009-04-13
Since PulseAudio works perfectly for most of it, it may be related to your sound hardware?

What is you sound card?
If it is Intel, did you test crimsun's .deb files in the pulseaudio sticky thread? Did they influence this behaviour?

---

### Post by viduliya on 2009-04-13
> **amano said:**
> Since PulseAudio works perfectly for most of it, it may be related to your sound hardware?


I find it hard to believe since I have issues in 3 different machines.  Machines 2 and 3 were upgraded from Intrepid.  Machine 1 was a clean install of Janty.

> **amano said:**
> 
What is you sound card?


```

Machine 1 (Desktop):
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

Machine 2 (Laptop with the kernel image .deb files from crimsun):
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)

Machine 3 (Laptop currently being rebuilt):
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```
> **amano said:**
> 
If it is Intel, did you test crimsun's .deb files in the pulseaudio sticky thread? Did they influence this behaviour?

Yes I did try the .deb files by crimsun on Machine 2 and it did not help the issues.  I still have issues on Machine 2 like very high CPU load when using Skype.

I tried to install a ppa to fix Machine 3 and it got wasted.  I will rebuild it.  I am planning on investigating the compatibility of that machine with dabien distro.

Machiene 1 is also experiancing problems of high CPU load and sound cutting in and out when using rythmbox.  It seems that this happens when I introduce other network traffic like loading the forum page.

Frankly, I am very surprised people are not having much issues with pulse audio on Janty.

---

### Post by viduliya on 2009-04-13
> **amano said:**
> 
If it is Intel, did you test crimsun's .deb files in the pulseaudio sticky thread? Did they influence this behaviour?

BTW, I assume that are referring to the .deb files at: [http://kernel.ubuntu.com/~dtchen/](http://kernel.ubuntu.com/~dtchen/)

---

### Post by markbuntu on 2009-04-13
Skype is still a poorly written buggy application so you really can't blame pulseaudio for that. 

Crimsun has been tearing his hair out trying to stabilize pulse0.9.14 for jaunty which everyone thinks is a bad idea but the decision to use 0.9.14 in jaunty has been written in stone. Months ago Lennart, the lead pulse developer, was telling everyone not to use 0.9.14 and wait for 0.9.15.

Updates have regularly made pulse worse and then better since alpha4 so.....

With any luck this will all get fixed by Koala.

---

### Post by avb on 2009-04-13
> Skype is still a poorly written buggy application so you really can't blame pulseaudio for that. 

thats just ridicoulus phrase. Skype works good without pulseaudio. So what is shitty written is a pulseaudio, unfortunately. Luckily its working more or less suitable. Sounds servers should work *transparently* in the system and not make decissions like what application is shitty or not.

---

### Post by viduliya on 2009-04-13
> **markbuntu said:**
> Skype is still a poorly written buggy application so you really can't blame pulseaudio for that. 

Crimsun has been tearing his hair out trying to stabilize pulse0.9.14 for jaunty which everyone thinks is a bad idea but the decision to use 0.9.14 in jaunty has been written in stone. Months ago Lennart, the lead pulse developer, was telling everyone not to use 0.9.14 and wait for 0.9.15.

Updates have regularly made pulse worse and then better since alpha4 so.....

With any luck this will all get fixed by Koala.

Hey, don't get me wrong. I am not dissing the efforts of those who are trying to make pulseaudio better.  I am simply looking for an alternative method to keep skype working along with other Apps.  Currently pulseaudio does seem to use too much more CPU even without the help of Skype.  I had a lot of fun during the Hardy upgrade with pulseaudio and I am not looking forward to that much fun with the Janty upgrade.

I doubt users will stop using an app like Skype for the sake of pulseaudio.  I don't understand what the rush was to push pulseaudio to be default and I don't see what I have gained by using pulseaudio over alsa and esd which used to just work without all this trouble.

Even now I am looking at my Machine 2 where sound and video don't even sync in totem when viewing streaming content.  All these machines will need to be rolled back to intrepid or something else.

---

### Post by markbuntu on 2009-04-13
> **avb said:**
> > Skype is still a poorly written buggy application so you really can't blame pulseaudio for that. 

thats just ridicoulus phrase. Skype works good without pulseaudio. So what is shitty written is a pulseaudio, unfortunately. Luckily its working more or less suitable. Sounds servers should work *transparently* in the system and not make decissions like what application is shitty or not.

Well, the skype devs made a lot of assumptions about controlling hardware when coding ther alsa driver, they still do. While skype works with alsa, it is not doing so properly and sooner or later that would have led to even bigger problems. Wine had the same problem but at least the wine devs fessed up about it and even the audacity devs have been working to fix their code.

Pulseaudio strictly enforces the new protocol to provide a security layer between applications and the drivers in the kernel. This was not necessary when the alsa drivers were not part of the kernel but now that they are, it is. Rewriting the alsa stack to account for this was basically impossible so something was needed. Even though Lennart said pulse was not quite ready and many applications were not either, pulse did enforce the new protocols. 

Pulse became widely adopted and many applications failed. This was a deliberate effort of the distro maintainers and kernel devs to push the application devs to fix their no longer acceptable code and maintain kernel security.

If you have issues with this, take it up with Linus Torvalds.

---

### Post by viduliya on 2009-04-13
> **markbuntu said:**
> Pulse became widely adopted and many applications failed. This was a deliberate effort of the distro maintainers and kernel devs to push the application devs to fix their no longer acceptable code and maintain kernel security.

If you have issues with this, take it up with Linus Torvalds.

This type of approach seem a bit extreme to me.  Users just want to have a usable system.  I always thought if pulse is the way to go then it should be integrated only when it is able to handle common apps.  When I was using Gentoo similar push happened when moving from static devices to udev.  But I don't recall it being so painful.

---

### Post by markbuntu on 2009-04-14
> **viduliya said:**
> This type of approach seem a bit extreme to me.  Users just want to have a usable system.  I always thought if pulse is the way to go then it should be integrated only when it is able to handle common apps.  When I was using Gentoo similar push happened when moving from static devices to udev.  But I don't recall it being so painful.

Well, the app devs were just dragging their feet and ignoring the issue. Is it reasonable to hold everything up just because skype and wine and audacity can't get their act together while hundreds of other app devs did?

Now it is the kernel teams turn. To handle many devices and produce quality glitch free sound the new pulseaudio needs full PREMPT and HZ=1000. This is going to cause problems with hoggy drivers that do not work with full PREEMPT or HZ=1000. PREMPT and HZ=100 is supposedly not used to accommodate nvidia blobs but this does not make any sense since nvidia works with rt kernels. Maybe it is time to merge rt patches into main.

---

### Post by avb on 2009-04-15
> **markbuntu said:**
> 
Pulse became widely adopted and many applications failed. This was a deliberate effort of the distro maintainers and kernel devs to push the application devs to fix their no longer acceptable code and maintain kernel security.


I dont care about how shitty is a code. All i care is stable and fast work.
Nothing is perfect in this world. Linux in general has a 'shitty' code in compare to netbsd but its works everywhere what u cant say about netbsd. 
About 5 years i cant use internal microphone, i never could use my softmodem and u talking about code quality. I dont care much, coz there is no other ways. But my coworkers all the time says 'wtf' to this. And they are right here. 

Id love to have one release with which i will be completely satisfied and just forget about any updates except security.

---

### Post by avb on 2009-04-15
BTW, you could listen mp3 music on pent-90mhz without any problems. Now only pulseaudio itself consume 10% of my core2duo 2ghz. Plus audio player. 
For me thats where shitty code is. Sure, coz core coding is so hard, lets build one more library on top of everything for simplification. Than we are coming to libxxx->gstreamer->pulseaudio->alsa->soundcard. Ah, i forget. Its not libxxx, its libcanberra. Its already invented. Sure, issue is in protocol. No questions about it.

---

### Post by lithorus on 2009-04-15
For pulseaudio 0.9.15 look here :
[http://ubuntuforums.org/showthread.php?t=1066212](http://ubuntuforums.org/showthread.php?t=1066212)

---

### Post by Flag on 2009-04-15
Can anybody pls. be so kind to explain to me why Skype works with PA in 8.04 and doesn't in 8.10 and 9.04?
I'm using Skype daily and is a MUST for me, for this I skipped 8.10 and by the looks of it will skip 9.04.

---

### Post by dino99 on 2009-04-15
ten minutes ago, i update jaunty and a new pulseaudio coming from ppa take place. to test it , i load streamtuner and no sound at all: conection refused (it was working just before); so i need to do: pulseaudio -k then pulseaudio -vvv and now sound is ok

---

### Post by lithorus on 2009-04-15
> **dino99 said:**
> ten minutes ago, i update jaunty and a new pulseaudio coming from ppa take place. to test it , i load streamtuner and no sound at all: conection refused (it was working just before); so i need to do: pulseaudio -k then pulseaudio -vvv and now sound is ok
A reboot would probably also have solved it.

---

