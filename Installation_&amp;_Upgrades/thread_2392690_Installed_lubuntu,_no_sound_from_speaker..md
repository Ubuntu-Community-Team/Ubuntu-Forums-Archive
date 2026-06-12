---
title: "Installed lubuntu, no sound from speaker."
date: 2018-05-24
forum: Installation &amp; Upgrades
---

### Post by enigma9o7 on 2018-05-24
Had an old Pentium 4 and decided to make it useful again.  After a little research, decided lubuntu was the way to go, wiped xp and installed lubuntu-18.04-desktop-i386 no problems other than it hung after it said installation was complete.  I sat there watching the 5 dots for half an hour (thinking maybe it was still doing something) before finally deciding to hit some keys, ESC showed me some type of terminal window and something about reboot failing, so I just rebooted and then all was well - except-

There's no sound from the internal speaker (which worked fine under XP).

Under sound settings by clicking on the speaker on the taskbar, I have two output device ports - headphones/Amplifier and Headphones/No Amplifier.  Tried both.  On the playback tab, when sound is playing (from firefox/youtube as I havent installed anything yet and that's the first thing I thought of to keep playing) it shows the firefox audiostream doing its thing...

Alsamixer had "Master Mono" set to zero, but maxing that out doesn't do anything.

I havent tested headphones.

Model: HP-d530-CMT
Alsamixer identifies Intel ICH5 / Analog Devices AD1981B

---

### Post by lbl2 on 2018-05-24
Please check for more updates first.

---

### Post by enigma9o7 on 2018-05-25
I'm not sure I understand.  I did the automatic update after install...

FYI, I tried xenialpup and it has sound out of the box.  But it's crazy slow, slower than xp and very unresponsive, which surprised me.

---

### Post by poorguy on 2018-05-26
Go to the ***software manager***  download and install  ***pulse audio volume control*** if it is not installed and that may fix the issue although no guarantees.


How much memory does your computer have installed.

If you are running only*** 512mb memory*** it will be slow I recommend at minimum ***1.0 GB memory***.

---

### Post by enigma9o7 on 2018-05-27
Thanks much, I'll give that a try.

And yeah, only half gig of memory.  I personally recommend 16GB, but that doesn't change the fact I'm trying to find an OS for a PC with 512mb I don't plan on spending any money on.   Anyways I was only commenting about xenial being surprisingly slow, the important fact is that sound worked, and I'm trying to get sound to work on lubuntu, and I doubt more memory will solve that.  If Lubuntu turns out to be too slow, I'll try DSL, or just give up and keep using XP.

---

### Post by poorguy on 2018-05-27
> **enigma9o7 said:**
> Thanks much, I'll give that a try.

And yeah, only half gig of memory.  I personally recommend 16GB, but that doesn't change the fact I'm trying to find an OS for a PC with 512mb I don't plan on spending any money on.   Anyways I was only commenting about xenial being surprisingly slow, the important fact is that sound worked, and I'm trying to get sound to work on lubuntu, and I doubt more memory will solve that.  If Lubuntu turns out to be too slow, I'll try DSL, or just give up and keep using XP.

I never said adding more memory would help the problem with sound that was what you assumed.

What I mentioned about memory was about the slowness of Linux due to the possibility of only running 512 mb ram.

---

### Post by enigma9o7 on 2018-05-28
Didn't get a chance right away to try that as I have family visiting for the holiday weekend.  Anyways software manager says I already have that installed.  And as I haven't installed anything since updates, it must have been included with Lubuntu.   In fact, in my initial post when I was referring to sound settings by clicking on the speaker on the taskbar, that is PuseAudio System Tray and brings up that is PulseAudio Volume Control.

Any other ideas?  I was kinda hoping there was something I could look at in Xenial that might be useful to setting Lubuntu?  

For reference, my only significant experience with unix was back in the day when the only internet access available was dial-up shell accounts, but of course that's pure text and I wasn't admin, so the only relevant experience is familiarity with command line file management, and the only software I really ran was pine (email), irc, ftp, fsp, and downloading (sz) stuff back to own PC.  And I was too lazy to learn to use vi so used pico for text editing.  Back then the web didn't have much and although I recall lynx was the web browser, nothing I cared about was on the web back then.  Later when SLIP/PPP became available I think I may have tried to get X-windows working but at 9600bps it wasn't usable, but it was nice being able to telnet/ftp from my own pc or open multiple shells w/o using screen.   Anyways I'll stop this ramble.

But I do want sound.

---

### Post by poorguy on 2018-05-28
Perhaps this link may be of help.

[https://ubuntuforums.org/showthread.php?t=2130640](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by enigma9o7 on 2018-05-28
Thanks much.  Lotsa reading there, and I did read the entire first page, and found it useful.  Some of it is outdated as, for example, it says to install that puleseaudio just like you did, however as I said it's already installed by default.  The main takeaway was giving me confidence lubuntu was the right choice, and reinforcing reasons not to use DSL if I do decide to go for another distro!   And I've opened the sound troubleshooting thread he linked and will read that next.  I was really expecting there'd be a simple answer that didn't require so much research tho!

---

### Post by poorguy on 2018-05-28
Perhaps a better option might be to find a newer used sound card which is better supported which I have had to do myself as I use eight year old and ten year old computers and hardware.

---

### Post by enigma9o7 on 2018-05-28
btw, headphones work, if that helps with ideas...

---

### Post by poorguy on 2018-05-28
You keep talking about the ***internal speaker*** have you tried connecting a real set of ***external speakers ***perhaps they may work.

The only ***internal speakers*** I've seen on a desktop were inside of the monitor and had a cable which had to be plugged into the output jack on the sound card / audio jack on the motherboard. 

I know there use to be a very small speaker inside of the computer case which was only for troubleshooting beeps codes.

---

### Post by mörgæs on 2018-05-28
> **enigma9o7 said:**
> Some of it is outdated as, for example, it says to install that pulseaudio just like you did, however as I said it's already installed by default.

Thanks for pointing that out. Correct, it's a default package in 18.04. Edited now.

---

### Post by enigma9o7 on 2018-05-28
Please stop suggesting I buy something. The whole point is I'm trying to setup a PC I have.  It isn't worth spending a single dollar on, but I don't mind spending some time.  I assume if it works under Xenial then there will be a way to make it work under Lubuntu, since they're both some type of ubuntu - or am I wrong in this assumption?  I assume that means they can use the same software or drivers or whatever is necessary to fix this.

Besides, I have a speaker plugged into the headphone jack until I figure out how to use the internal speaker.

---

### Post by enigma9o7 on 2018-05-28
> **poorguy said:**
> You keep talking about the ***internal speaker*** have you tried connecting a real set of ***external speakers ***perhaps they may work.

The only ***internal speakers*** I've seen on a  desktop were inside of the monitor and had a cable which had to be  plugged into the output jack on the sound card / audio jack on the  motherboard. 

I know there use to be a very small speaker inside of the computer case which was only for troubleshooting beeps codes.

Yes, external speakers work - you posted that after I'd mentioned headphones work, but I have tried both the front headphone jack and the rear speaker jack, bothfine.  That's the amplified vs. non amplied outputs.  But this has a real internal speaker like a laptop, not just the pc speaker that usually comes with your case and is actually much bigger than motherboard speaker.   As I've said it works perfectly fine in XP and Xenial.

---

### Post by enigma9o7 on 2018-05-28
> **mörgæs said:**
> Thanks for pointing that out. Correct, it's a default package in 18.04. Edited now.

You're very welcome!  Thanks for the helpful thread.  By the way, OS's are called operating system's just because that's what they've historically been called.  Nobody's ever called them operative systems, so we don't say that, although operative is certainly a word, means something like working/functional or sometimes in context it means the most most important detail. Also in context it can mean special agent like CIA/MI6/etc who works out of the office (in the field).

---

### Post by poorguy on 2018-05-28
Since external speakers work then I would have to say that perhaps the problem with the internal speakers may have something to do with a sound configuration setting. 

Perhaps someone more familiar with this type of setup can offer better advice.

---

### Post by jimray on 2018-05-29
I have had similar experience and I am sure many people here have too. Strange thing about mine is one minute the internal speaker is okay, the next its external speaker. Updates solved the problem for me and I think the consistency of this problem was because most times I used an old hardware for my setup.

---

### Post by enigma9o7 on 2018-05-31
Quite frustrating, but I think I'm going to give up and try yet another linux distro.  I've spent so much time trying to make this sound work and although I've learned something, I haven't gotten any closer to a solution.   I guess I'll shrink the partition and save it incase I change my mind later or someone posts another idea to try.

---

### Post by enigma9o7 on 2018-06-03
Just a little more info, as I actually did try another distro, and it too has the same audio issue with pulse, and I think I at least have an idea of the problem, and it is pulse lacking the control I need - I need another mixer or a change made to pulse (is this possible?  I didn't even think of that til I typed it, I'm going to search after I post this.)

In Puppylinux, which uses retrovol, I can turn off (or down the  slider) everything except PCM and MASTER MONO.   Both of these sliders  affect volume, and if either one is all the way down or turned off, no  sound.   Additionally the mono output select has to be set to "mix" as  opposed to "mic".  Other than that, the rest of the sliders and settings  have no affect.    	  

  In lubuntu, I can see when I run alsamixer than Master  Mono is turned off.  I can turn it up in there but it doesn't change  anything.   Additionally it says "MM" instead of numbers even when I  turn it up, so I think that's the problem.  But how to fix?   Apperantly  retrovol is only for puppy linux so I can't install that here to try  easily (can I?  I have a live CD can I copy something off it?).      

   	  

   	I think w**hat I need is a replacement pulse audio mixer than either has Master Mono enabled by default, or gives me control of it**.   Additionally for volume control I need to be able to control master mono or PCM because master doesn't do anything.

---

### Post by enigma9o7 on 2018-06-04
I figured out how to use alsamixer. Hitting 'm' to for mute/unmute.  so all I have to do is unmute 'master mono' and turn up the slider, then I have sound in lubuntu.

Now how to make that stick is the next question....

---

### Post by enigma9o7 on 2018-06-04
Well I now figured out how to turn it on from command line.  How do I autoexecute this at startup?
amixer cset name='Master Mono Playback Switch' 1
amixer set 'Master Mono' 100

---

