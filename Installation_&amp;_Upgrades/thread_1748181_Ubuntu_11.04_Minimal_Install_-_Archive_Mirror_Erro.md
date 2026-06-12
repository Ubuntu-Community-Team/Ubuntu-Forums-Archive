---
title: "Ubuntu 11.04 Minimal Install - Archive Mirror Errors"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by MattMc3 on 2011-05-03
I'm trying to do a clean minimal install of Ubuntu v11.04 (not an upgrade). I've downloaded the "mini.iso" from [here]("https://help.ubuntu.com/community/Installation/MinimalCD") (32-bit PC x86) and burned it to a CD. This is how far I can get before I get mirror errors:

- Boot from the CD, select "Command Line Install" option
- Select a language: English (Default)
- Select your location: United States (Default)
- Detect keyboard layout: No (Default)
- Configure the keyboard: USA (Default)
- Configure the keyboard layout: USA (Default)
- Configure the network hardware with DHCP: Successful
- Configure the network hostname: Ubuntu (Default)
- Choose a mirror of the Ubuntu archive: United States (Default)
- Ubuntu archive mirror: US.ARCHIVE.UBUNTU.COM (Default)
- HTTP proxy information: Blank (Default)
- Loading additional components: Successfully downloads files to 100%
- Setting up the clock - Getting time from local server
- Configuring the clock: America, Los Angeles (Default)
- Detecting disk and other hardware: "The installer failed to download a file from the mirror. This may be a problem with your network, or with the mirror. You can choose to retry the download, select a different mirror, or cancel and choose another installation method."
- If I choose "Retry" I get the same error instantly.
- If I choose "Change Mirror", the "Ubuntu archive mirror country" screen come up. Selecting any country option from that page comes up with a red screen that says "Bad archive mirror. An error has been detected while trying to use the specified Ubuntu archive mirror."

Earlier in the installation, when I chose "US.ARCHIVE.UBUNTU.COM", the installation successfully downloaded files and detects the correct time zone, but later on it fails when it tries to download from any archive mirror. A couple of months ago I successfully did a clean install of Ubuntu 10.04 LTS minimal install. I did not have to use any custom settings for DHCP or proxy then. 

Any suggestions? Thanks.

Matthew

---

### Post by mörgæs on 2011-05-03
Here is the mirror list:

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

Do you get contact using any of these?

---

### Post by MattMc3 on 2011-05-03
Thanks for the reply. I wrote a few of those mirrors down and tried it again, but I couldn't find anywhere to input them during the install. The only choices I can make are to choose a country and select the default mirror (for that country). I didn't see anywhere to manually type in an address. According to the on-screen prompts, my only choices are tab, space bar (select) and enter.

There is good news though. This time during the installation, after my mirror errors were displayed, I "esc"aped out of the installation and for some reason it continued on to the partition page. After partitioning/configuring the install drive the installation continued normally (I tried that once before - it partitioned correctly but nothing downloaded). This time all the files downloaded correctly. I was using the 64-bit minimal install cd this time, so I'm going to retry with the 32-bit cd and see what happens.

Matthew

Edit: I found out where to input the mirror addresses but I still couldn't get it working.

---

### Post by MattMc3 on 2011-05-03
I gave it the ol' community college try and quit after a five or six tries. That one time it fully loaded it would only boot to a black screen. I tried installing it with both with the 32-bit and 64-bit versions and couldn't get it to work. I went back to the Ubuntu v10.04 LTS minimal install CD and it worked perfectly the first time. It's supported for two more years so I'll just stick with that.

Matthew

---

### Post by rleck on 2011-05-15
**This is not related to the main issue of missing mirrors**

If you get stuck at a black screen after an upgrade or a command line install of 11.04, use Ctr-Alt-F1 to switch to tty1 (terminal 1) to log in. Your system probably isn't broken at all. It's likely to be the bug in grub2: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/761830](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/761830)
Don't give up - Natty is cool!

---

### Post by G-forze on 2011-05-19
I have the same problem with the failing mirrors. Trying to install Ubuntu server (natty) on a Intel Atom htpc, installing from USB. The first time I tried installing it got all the way to letting me specify server components (DNS, mail...) before it started complaining about the mirrors. Subsequent tries have not gone even that far.

I tried first with the alternate install (am setting up a RAID), and then switched to ordinary server to no avail. There is no problem downloading components before partitioning, but afterwards it immediately fails with the "Bad address" -message mentioned by thread starter.

If I go into shell mode I can check the syslog at /var/log/syslog and it contains an INFO: mirror does not have any suite symlinks, and a WARNING: mirror does not support the specified version (natty) [or something to that effect, had to write from memory]. If I try to wget the addresses manually the result is "Bad address", but that could just be me not knowing the ins and outs of wget.

Any help? I'd really like to have Natty installed.

---

### Post by G-forze on 2011-05-19
Hi again.

I fixed the problem - sort of. When the error message came up, I went back to the network configuration and had it detected and configured again. After that the installer picked up where it had left off and went on installing the whole system without a hick-up. 

Beats me what the real problem was, but since so many others are experiencing the same and it was so unpredictable, I still think it is a bug in the handling of the mirrors.

---

### Post by solitario on 2012-08-02
Sorry. I know it's an old thread, but just wanted to say I'm having the same problem. Unfortunately the prompt will not allow me to enter a different mirror.

---

### Post by oldos2er on 2012-08-02
Old thread closed. Please start a new thread for your question.

---

