---
title: "Problem with Intel-HDA"
date: 2009-03-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by NK-Magi on 2009-03-03
Hello there,

Currently running Interepid Ibex on my new-ish HP dv4-1117nr with an Intel-HDA-ICH9 sound card in it.  Ibex ran fine on my laptop but started with choppy sound fixed by adding in the "msi_enabled=1" tag onto /etc/modprobe.d/alsa-base about a month ago, but the gnome-power-manager kept crashing on every battery unplug so I went back to Windows.  Recently though, I decided to try out Jaunty to hope the newer packages and kernel would fix my problems.

They did to an extent, the battery is wonderful now and everything fit into place nicely except now sound doesn't work at all, I just reformatted and was going to try some other things to hopefully get it to work including trying the msi_enable=1 trick before upgrading to Jaunty, but in Jaunty I tried both the msi trick, compiling alsa from source, and a few other methods defined on the Intel-HDA help page with no prevail.

The headphone jack doesn't work either, and I'm having to shove blame on either the new alsa, pulseaudio, or kernel.  Any suggestions on how to fix this to get Jaunty up and running?

---

### Post by crimsun on 2009-03-03
Firstly, I need the output from [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) run on both your 8.10 and 9.04 installs.

Secondly, make sure you add my PPA for a testing PulseAudio.

I presume that you will be reporting back with pristine installations for both (i.e., no self-compiled PulseAudio, ALSA-*, etc.).

---

### Post by NK-Magi on 2009-03-04
Mmk, my information of 8.10 is at: [http://www.alsa-project.org/db/?f=2932e0e464c20c06e824a413c06e265315558c5f](http://www.alsa-project.org/db/?f=2932e0e464c20c06e824a413c06e265315558c5f)

Looking at it, it seems like my soundcard isn't installed with alsa (best guess).

I also added your personal PPA but it didn't change anything along the lines of my packages, only updated 2 libraries that I'd guess were normal updates, nothing sound related.

And also I am running on pristine installs like you said, I'm not gonna get started on configuring everything if I can't get all the parts working (the only other thing broke is the mute button on the touch controls is always red in 9.04 which won't be anything big and the IR remote isn't working which I never use anyway and all of this might be fixed later on after a few kernel updates).

---

### Post by berthiggins on 2009-03-04
I have an hp 6530b laptop and I had to add 
options snd-hda-intel model=laptop enable=1 index=0
to /etc/modprobe.d/options to get sound.
It seems that the driver can't find the internal speakers without it 
My sound now works fine 
Hope this helps.

---

### Post by NK-Magi on 2009-03-04
Hmm, I tried that option berthiggins, but it didn't change anything.  I also tried it in tandem with the "options snd-hda-intel model=3stack-dig enable_msi=1" I found on Google that's supposed to remedy most of the HP laptops.

After a fresh install of 8.10 at noon for that alsa-info, I used update-manager -d to move onto 9.04 and this is the new alsa-info: [http://www.alsa-project.org/db/?f=5b94761f18790ad287cd4f1d05c90074f3e82b07](http://www.alsa-project.org/db/?f=5b94761f18790ad287cd4f1d05c90074f3e82b07)

Any other suggestions?

---

### Post by NK-Magi on 2009-03-04
Mmk, I forgot to add in a line for your PPA and now its working and authenticated and I updated my pulseaudio, but it didn't change anything.  Tried it with berthiggins suggestion and the enable_msi=1 and model=3stack-dig with no changes.\

About to try the 64-bit version for hopefully different results (I've got 4 gigs of ram so it'll only end up being a plus I suppose)

---

### Post by NK-Magi on 2009-03-04
Yet another update!

I've finally got sound, I installed the 2.9.29r7 kernel from the deb's off of Ubuntu's website and now sound works.  But the problem now is that it ruined my touch wireless switch and won't turn on my Broadcom BCM4312 Wireless card.

My guess now is that my card is supported by the new kernel but somewhere along the line my wi-fi got messed up.  Gonna try a few more things to maybe fix it.

---

### Post by Nullack on 2009-03-04
By going to an unsupported kernel, your, well, unsupported :)

Note that Jaunty has a bunch of Intel HDA changes in recent GIT changes for the supported kernel.

---

### Post by marttali on 2009-03-05
Hey, just a thing that might fix many of your problems  - update your machine BIOS!

---

### Post by NK-Magi on 2009-03-05
Haha of course an unsupported kernel will mess things up :P, I'm going to try it without the properitary driver and the new kernel.

Before I was hoping to get better ACPI performance when I was running windows so I'm already running the latest Bios (F.24).

---

### Post by NK-Magi on 2009-03-05
Mmk, Sound works fine with 2.6.29-rc7 but I'm stuck without Wi-Fi, I tried ndiswrapper but I couldn't compile the module with this newer kernel, no support.  I also tried using the bw43-cutter but that didn't work either for this Broadcom chip :(.  I guess I'ma stick with Intrepid until the Jaunty beta comes out with a new restricted-headers package.

---

### Post by Ubuntiac on 2009-04-03
I'm in the exact same situation with an HP Mini 1010NR.

So speaker sound unless I use the 2.6.29 kernel which doesn't support my broadcom wireless. So does this mean that this problem is likely to be fixed for the 2.6.28 kernel by the next packaging of restricted-headers, or are we talking waiting until the release of Karmic for a supported fix here?

---

