---
title: "v4l2 problems with pinnacle 800i"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by apt94jesse on 2008-01-23
Hello all,

As someone new to ubuntu and linux as a whole, I've enjoyed the learning process and tried to stay off the forums with the noob questions as much as possible.  But I'm officially stumped.

I'm trying to install a Pinnacle pctv hd 800i card in my box.  According to this link:

[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i))

the support is now relatively stable, as the page was updated Jan 16th '08.

The card was recognized before attempting to install the drivers, but mythtv couldn't find it, so I assumed I needed to install drivers (similar to getting the linksys wireless adapter drivers into the restricted driver database).

So I fumbled my way through the instructions, finally thinking I had succeeded because "v4l2-int-device" showed up in my Restricted Drivers menu.

However, upon restart, the ubuntu splash screen loads, the bar fills, and then... BLACK.  and nothing more.

Removing the card allows me to boot all the way into gnome with no problems.  I'm assuming I need to remove the drivers and start from scratch.

HOW DO I REMOVE THESE DRIVERS AND FILES?  It's killing me, and I'm sure its simple.  I've removed the files and folders I downloaded and installed from, but it still shows up, and upon re-installation of the card, I still get the blank screen.

No reference to the driver in xorg.conf, either.

Any insight is greatly appreciated.  Thanks in advance.

-Jesse

---

### Post by mikehow on 2008-01-23
Glad (not that it helps the situation) to see that I'm not the only person that this has happened to.  I'm gonna keep on messing with it, and I'll post more if I get it to work or not.  I can get the video to work through tvtime under the composite 2, but no sound.

---

### Post by mikehow on 2008-01-23
Luckily, I have got Ubuntu on livecd because after I did exactly what the website, [http://linuxtv.org/repo/](http://linuxtv.org/repo/), said to do to install the kernel, Ubuntu locked up when it was loading up.  It made it to the U, but made it no further.  Let it sit like that for five minutes and nothing.  I emailed Steven Toth, the writer for the kernel, and all he did was refer me to the wiki.  :).  So emailing him is a waste of time.  Will try something different tomorrow.  Found, [http://www.gossamer-threads.com/lists/mythtv/users/310806](http://www.gossamer-threads.com/lists/mythtv/users/310806),  I'm going to try and email that guy to see what he did.  Hopefully, he'll respond a little nicer than Steven "No Help" Toth.

---

### Post by apt94jesse on 2008-01-23
Sounds like a plan, I read through that link you posted and it gives me hope to hear that someone else actually got the card working with myth.  I'll hold off on emailing him myself to keep from bombarding his inbox.

Did you try to take the card out to fix the blank screen issue?  I'd REALLY rather not format the disk and start from scratch if I don't have to, but it may be my only option :(

Does anyone else know how to erase any trace of the v4l-dvb stuff?  I went through synaptic package manager and got rid of the stuff I could find, but its possible if I missed something.  Or maybe I just don't know where to look in the file system to delete the files.

If I can get back to square one (booting successfully WITH the card installed), I'd feel a lot better.

Mike, thanks for the help so far, and good luck.

Jesse

---

### Post by DamnYankee on 2008-01-24
I'm the guy in the other forum who got my Pinnacle 800i to work.

I am using Mythdora so I have no experience with Ubuntu.
 
I downloaded the driver from [http://www.linuxtv.org/hg/v4l-dvb/](http://www.linuxtv.org/hg/v4l-dvb/) by selecting bz2 or gz at the top of the page.
 
I then untarred the files and went into the directory and did make to compile then make install.
 
Good luck and please feel free to ask more questions if you like.
 
Tim

---

### Post by DamnYankee on 2008-01-24
Also,

Do you have the firmware for the xc5000 tuner in place? If not, then please download it from [http://www.steventoth.net/linux/xc5000/](http://www.steventoth.net/linux/xc5000/) and extract the firmware using the script in the same location (see the readme file for instruction). I hope that will resolve the issue.

Tim

---

### Post by apt94jesse on 2008-01-24
Tim, thanks for joining in!

I think I'll try to to follow those steps without undoing my previous changes.  Can't do any more harm, I guess.

For the XC5000, what is that?  Is it onboard the 800i?  Just asking because this is the first I've heard of it.

Thanks again, I feel a long lunch break coming on to see if I can get it working.

Jesse

---

### Post by DamnYankee on 2008-01-24
Yes the XC5000 is a tuner chip on the 800i and if you do not have the firmware available for it when the driver loads *bad things* happen.

I think there is some reference to it on the wiki page.

[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29)

Tim

---

### Post by apt94jesse on 2008-01-24
Tim, you're my hero, man!  The XC5000 firmware was the key.  Extracted the firmware from the archive, moved the file into /lib/firmware, shut down, re-inserted the card, booted, crossed fingers... voila, beautiful.

Mythtv recognized the card right away!

I still have some input issues with the cabling, but the card seems to be working flawlessly (knock on wood).

Thanks guys, Awesome stuff.

-Jesse

---

### Post by DamnYankee on 2008-01-24
Glad to hear it!

If/when you get around to the remote I can share what I did.  That is my first remote on mythtv or even lirc so I am NO expert, but I did get it to work for me and I love it........

Tim

---

### Post by mikehow on 2008-01-24
kk I got ubuntu to recognize the device.  Or at least I think it did.  In dmesg I don't see the long post of all the different types of tuner cards.  In Hardware Information it has added "DVB Device" under CX23880/1/2/3 PCI Video and Audio Decoder.  I get video for Composite 1, S-video and Television under tvtime, but no audio.  In Mythtv, I get jack.  It says that it cannot load tuner.  What am I doing wrong?

---

### Post by apt94jesse on 2008-01-24
Mike,

are you talking about the process to extract the firmware for the cx5000?  If so, the command (inside the directory you have the files) is:

sudo sh extract.sh

that will produce a file that is the firmware you need to copy to the /lib/firmware directory.

That may be a Noob explanation, but I had to learn it as it was the first "sh" command I had to use.

You'll eventually have to restart I imagine.  If you get the problems, you should take the card out and continue to fine tune things.  At least that's what I did.

Just so you know Mike, my "restricted drivers" list had an entry for "v4l2-int-device" after I installed the driver, but no change after I added the firmware.  It had the red light "not in use" indicator next to it, but it was there.

Continued good luck.

Jesse

---

### Post by apt94jesse on 2008-01-24
Tim, how does your audio sound on your 800i?  Mine is very tinny... like its extremely overmodulated even at very low volumes.

I'm pretty sure its not the card just because its so bad.  I'm thinking its my mythtv settings.

Would you mind going through a quick overview of your audio setup (settings in the setup program, etc.)

Thanks, I'm really stoked that I got the video working, just gotta get the sound up to par and we're cookin with gas!

Jesse

---

### Post by apt94jesse on 2008-01-24
Solved!

[http://www.mythtv.org/wiki/index.php/Troubleshooting:Sound](http://www.mythtv.org/wiki/index.php/Troubleshooting:Sound)

I found the "distored audio on input" section.  Apparently myth defaults to lower mp3 encoding than optimum.  Just changed it in the options defined in the link above.

Jesse

---

### Post by DamnYankee on 2008-01-25
I had the same audio problem and found the same solution.

Glad you are making progress!

Tim

---

### Post by apt94jesse on 2008-01-26
Tim,

With your video, do you get horizontal line of distortion at the very top of your screen?  I'm trying to narrow it down and to see if its the card or something else.  Its just one line, probably the top one of the 480i signal.

It's not the inputs, as I've switched both the signal coming in and the input (composite, coax).

Not a serious problem, I guess, but since I'm switching from my set top box to my mythtv box, I'd like to duplicate the experience as closely as possible.

Thanks.

Jesse

---

### Post by PermuZero on 2008-01-26
That solved my sound issue as well, thanks a bunch.  Although I am also getting the like of distortion at the top of the screen.  Not a big deal, but would be nice to get rid of it.

---

### Post by DamnYankee on 2008-01-26
> **apt94jesse said:**
> Tim,

With your video, do you get horizontal line of distortion at the very top of your screen?  I'm trying to narrow it down and to see if its the card or something else.  Its just one line, probably the top one of the 480i signal.

It's not the inputs, as I've switched both the signal coming in and the input (composite, coax).

Not a serious problem, I guess, but since I'm switching from my set top box to my mythtv box, I'd like to duplicate the experience as closely as possible.

Thanks.

Jesse

I do get that distortion.

I *think* there is some configuration about overscan or some such that may get rid of it.  I have not researched it yet.  AND I may be completely off base......

Tim

---

### Post by apt94jesse on 2008-01-28
I am now getting an audio problem.  It happened when I switched the input from TV to Composite.  It showed the video from composite, but the audio from the tv input.  When the tv input was disconnected, all I got was static.

SO, I deleted the cards, sources, etc. and started over.  Now it doesn't give me the static and doesn't give me the tv audio on the composite input, BUT it doesn't give me the composite audio input.

I guess my question is: Is anyone using the composite input on this card?  If so, what are your settings (audio or anything that would influence audio)?

Thanks.

Jesse

---

