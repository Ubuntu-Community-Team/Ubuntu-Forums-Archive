---
title: "After a sudo apt-get command i lost all boot devies in my BIOS"
date: 2013-09-20
forum: Installation &amp; Upgrades
---

### Post by wdh1974 on 2013-09-20
I installed Lubuntu, and right at the onset it wasn't for me(though i could reboot just fine no issues), and i had  no sound. After lots of research i wasn't getting anywhere with my sound  problems, then i found this.........lol

sudo add-apt-repository  ppa:ubuntu-audio-dev/ppa; sudo apt-get update;sudo apt-get dist-upgrade;  sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils  gdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y  --reinstall install linux-sound-base alsa-base alsa-utils gdm  ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio;  rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group  | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e  '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'`  `whoami`

Well, that monster of a sudo command fixed my sound 100% lol, and after a reboot i had NO BOOT devices!!!

Ok  sicne i was already annoyed with Lubuntu i grabbed mint, made a  bootable USB, and all went well, installed, i could see my HDD in LIVE  mode, rebooted after the install compelted, pulled out the USB and BOOM  back in BIOS with no boot devices lol.

My laptop is a ASUS x401u, no optical drive just a HDD. It is UEFI

I cant help be laugh at my situation....[IMG]http://forums.linuxmint.com/images/smilies/icon_smile.gif[/IMG]

---

### Post by Quackers on 2013-09-20
A far as I'm aware nothing Lubuntu or mint-based could affect your bios boot devices. I'd be looking at your computer for answers not the OS.

And I think that huge command was actually separate commands.

---

### Post by wdh1974 on 2013-09-20
Yeah, i agree, but i i had rebooted several times before that command with no issues, then after that command, it's all gone, really weird. i mean nothing is listed lol, tho the mint OS is there as when i use the USB again to try and install  it asks if i want to overwrite the previous version of MINT. Ive done some google searching about adding a new boot option, but i cant find anything concrete.

---

### Post by Quackers on 2013-09-20
Try resetting the bios to default.

---

### Post by wdh1974 on 2013-09-20
yeah tried, its not working, maybe i need to move to the hardware forums?

---

### Post by Quackers on 2013-09-20
It's an odd one.  Maybe shut it down for a while and try again. I really don't know what to suggest.

---

### Post by wdh1974 on 2013-09-26
I just thought i should check back and let you know, or anyone that reads this that i figured it out. The problem was simply my MBR got destroyed from that command listen above, there can be no other reason i can see, before that command i rebooted many times before. either way, that was this issue lol.

---

