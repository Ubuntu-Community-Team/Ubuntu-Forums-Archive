---
title: "sb x-fi, alsa 1.0.18a, and intrepid"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by geoffjay on 2008-11-19
First off, I'm an idiot and didn't backup before getting into all this so a word from the not-so-wise - "backup your settings before trying to upgrade alsa."

# lspci | grep -i audio
03:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG

At first I followed:
  [http://lne.byexamples.com/?p=39](http://lne.byexamples.com/?p=39)
next I did:
  [http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106](http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106)
and finally:
  [http://ubuntuforums.org/showthread.php?t=962695&highlight=alsa+ca0106](http://ubuntuforums.org/showthread.php?t=962695&highlight=alsa+ca0106)

I followed the instructions from the first link on a fresh 8.10 installation, after each one things got worse and worse. After I reboot I get:

# lsmod | grep snd
snd_page_alloc       16776      0

so my first thought is that I must be loading the modules the wrong way or just the wrong modules altogether. If I run:

# sudo modprobe snd-ca0106 
# sudo modprobe snd-pcm-oss 
# sudo modprobe snd-mixer-oss 
# sudo modprobe snd-seq-oss

Then I get the following error if I try to restart alsa:
# sudo /etc/init.d/alsasound restart

Shutting down sound driver: /usr/sbin/alsactl: save_state:1513: No soundcards found...
done
Starting sound driver: snd-ca0106 done
/usr/sbin/alsactl: load_state:1616: No soundcards found...

Where should I be loading my soundcard from? I thought /etc/modprobe.d/alsa-base so I took a look through there and I can't find an entry for snd-ca0106, do I need to manually add an entry here?

Can anybody help? Pretty please.

---

### Post by geoffjay on 2008-11-19
I re-ran the script in the third link that I listed, only this time I removed the files that I had downloaded from the alsa site and let the script do it using the -f option and I'm now back where I was to begin with. 

What I didn't mention in my last post was that I have 2 sound devices, one on-board that uses the snd_hda_intel driver and an x-fi card that uses the snd_ca0106 driver, it's the on-board card that I have working again. I'm going to try using the script again but first edit the configure file to use the driver that I want.

Is there anybody that's successfully installed this card before?

---

