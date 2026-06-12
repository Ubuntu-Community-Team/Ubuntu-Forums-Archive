---
title: "How to get audio thru HDMI on GIGABYTE GA-73PVM-S2H"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by bmwman on 2008-08-28
I just installed Mythbuntu 8.04.1 on my new motherboard. Everything seems to be working fine, but I can't hear any sound. I'm connected to my 50" TV via HDMI and can get 1080p resolution with no problem. I tried turning the volume up on every sound slider  but still nothing. 

What do I need to do to make it work? Is there any special tweaks or tricks to redirect the sound to HDMI?

Thank in advance.

---

### Post by kaivalagi on 2008-08-28
> **bmwman said:**
> I just installed Mythbuntu 8.04.1 on my new motherboard. Everything seems to be working fine, but I can't hear any sound. I'm connected to my 50" TV via HDMI and can get 1080p resolution with no problem. I tried turning the volume up on every sound slider  but still nothing. 

What do I need to do to make it work? Is there any special tweaks or tricks to redirect the sound to HDMI?

Thank in advance.

Can't help you on the audio through hdmi front, I don't have sound output turned on the tv, all mine goes through optical to my amp...

This issue might not be the mobo, I remember see some posts about sound thru hdmi in general before now, I can't remember where though, maybe search the forums here if you haven't done so already?

---

### Post by bmwman on 2008-08-28
I saw a few but they were all for ATI and not NVIDIA. I couln't find anything about NVDIA so far.

---

### Post by bmwman on 2008-08-28
I just read that the Nvidia 169.XXx driver may not support the audio but i can try updating it to the newest driver tonight. Also does anybody knows which version of ALSA comes with 8.04.1 in case I need to upgrade to newer one and do I upgrade ALSA first and then load the new Nvidia driver(I believe it's 174.xxx) or the other way around?

Thanks.

---

### Post by kaivalagi on 2008-08-28
> **bmwman said:**
> I just read that the Nvidia 169.XXx driver may not support the audio but i can try updating it to the newest driver tonight. Also does anybody knows which version of ALSA comes with 8.04.1 in case I need to upgrade to newer one and do I upgrade ALSA first and then load the new Nvidia driver(I believe it's 174.xxx) or the other way around?

Thanks.

Use envy to install the latest nvidia drivers, I am pretty sure what you'll get through that are new enough. EnvyNG is here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

For alsa have a look at the the realtek site here: [http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

If I remember rightly when I was running gutsy I used the hd audio linux drivers from there to setup the latest version of alsa, they had a nice install script with them....not sure what version of alsa they are and whether they will do the job but if they sort the problem it's the quickest and easiest route IMHO

Not sure on the order, I would suggest nvidia then alsa, as you want the sound to go through hsmi which is a nvidia thing....guessing though

---

### Post by bmwman on 2008-08-28
Well I installed the latest Nvidia driver with ENVYNG but I still don't see HDMI listed when I run alsamixer. BTW Alsa is 1.0.15

What should I do next?

---

### Post by kaivalagi on 2008-08-28
> **bmwman said:**
> Well I installed the latest Nvidia driver with ENVYNG but I still don't see HDMI listed when I run alsamixer. BTW Alsa is 1.0.15

What should I do next?

Swear!

I have no clue what you can try now...I would sure like to see the answer though...

---

### Post by bmwman on 2008-08-29
Can't believe there're over 80 views so far and nobody knows what how to make the sound thru HDMI works?!That's really hard to believe. Thought there're lot of hackers and knowledgeable people on here! I'm sure I'm not the only one using HDMI.

---

### Post by cooke77 on 2008-08-29
What sort of Sound-card are you using, with HDMI and Ubuntu?
If it is a PCI-E (Express or whatever the latest may be).......it has a Sound driver all of it's very own.
This 'conflicts'.....with the computer-based Sound. (Whether this may be 'on-board', or as an 'add-in card').
Will so often 'MUTE' Sound! 
Until 'conflict' is resolved.
Found this 'problem'.....with my ATI-based PCI-E Graphics-card (working under XP), a while back.
Changed it .......to a nVidia one. 
No problem, since.

IF Sound is Realtek-based, could explain everything.

Read a few more 'posts'...concerning Sound (and Realtek), you'll get what I mean, especially if Realtek is High Definition Audio.
 Solution?
If you can install one, get a Creative Labs Sound-card. (They are very well 'supported'.....of Linux.)

Last of all, maybe you should have checked this out, first......IS the ALSA Sound (itself) 'Muted', by any chance?

Fault-finding...is no different...in Linux, than it is in Windows. (Same principles do apply.)
When in doubt...go back to 'basics'.

---

### Post by bmwman on 2008-08-29
It's an onboard Realtek based. This is the model of the motherboard GIGABYTE GA-73PVM-S2H. Here you can see the full specs :

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128072](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128072)

The sound chipset is Realtek ALC889A, but in ALSA I see 882 for some reason. I do get sound thru the headphone jack but it really sucks and I do need to get it to go thru the HDMI because that's how I connect it to my home stereo.

Thanks in advance.

BTW I don't have Windows loaded on the machine, only Ubuntu.

---

### Post by BluJai on 2008-08-29
I've been experiencing the same issues with that motherboard. Research in general shows it to function (on Vista systems), so the hardware is obviously capable.

I'm going to look into some of the items mentioned when I return home and see if there is anything I can add to the discussion. I have the HDMI output connected straight to a 1080p HDTV's HDMI input.

- [COLOR="Blue"]Blu[/COLOR]Jai

---

### Post by bmwman on 2008-08-29
> **BluJai said:**
> I've been experiencing the same issues with that motherboard. Research in general shows it to function (on Vista systems), so the hardware is obviously capable.

I'm going to look into some of the items mentioned when I return home and see if there is anything I can add to the discussion. I have the HDMI output connected straight to a 1080p HDTV's HDMI input.

- [COLOR="Blue"]Blu[/COLOR]Jai

Same here, my HTPC is connected to my 50" plasma via HDMI. I've been reading on this for few days now and I think next thing I/m going to try installing the Realtek drivers. I wasn't sure if I have to remove the old driver and ALSA first but I looked at the install script in the Realtek drivers and it does it automatically.

---

### Post by kaivalagi on 2008-08-29
> **bmwman said:**
> Same here, my HTPC is connected to my 50" plasma via HDMI. I've been reading on this for few days now and I think next thing I/m going to try installing the Realtek drivers. I wasn't sure if I have to remove the old driver and ALSA first but I looked at the install script in the Realtek drivers and it does it automatically.

Like I said before, I used those drivers when I setup gutsy on the same mobo, they worked really well. Quite surprising for a manufacturer's own efforts!

No guarantee the HDMI audio will work though :(

I'm eager to know to outcome..

---

### Post by bmwman on 2008-08-29
Well that blows. I ran the install script. It started doing it's thing. First time it came up with an error for missin library which I figured out myself. I installed libncurses5-dev and tried again. This time it was compiling for quite a while and then came up with another error which I have no idea what it is. Here is the bottom of the script:

ake[1]: Leaving directory `/home/backend/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsactl'
Making install in alsaconf
make[1]: Entering directory `/home/backend/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf'
Making install in po
make[2]: Entering directory `/home/backend/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/backend/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf/po'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/backend/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf'
make: *** [install-recursive] Error 1
Remove Folder.....
./install: 101: alsaconf: not found

???

---

### Post by kaivalagi on 2008-08-29
> **bmwman said:**
> Well that blows. I ran the install script. It started doing it's thing. First time it came up with an error for missin library which I figured out myself. I installed libncurses5-dev and tried again. This time it was compiling for quite a while and then came up with another error which I have no idea what it is. Here is the bottom of the script:

ake[1]: Leaving directory `/home/backend/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsactl'
Making install in alsaconf
make[1]: Entering directory `/home/backend/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf'
Making install in po
make[2]: Entering directory `/home/backend/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/backend/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf/po'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/backend/Desktop/realtek-linux-audiopack-5.07/alsa-utils-1.0.16/alsaconf'
make: *** [install-recursive] Error 1
Remove Folder.....
./install: 101: alsaconf: not found

???

Ran as sudo? It's been a while but I think if you use the install script you need to run as sudo to do the "make install", alternatively you can do each step manually (configure/make/make install)

That's as much as I can remember...

---

### Post by bmwman on 2008-08-29
That's what I did. Ran it with "sudo" and ./configure was fine but it failed at "sudo make"

---

### Post by bmwman on 2008-08-29
I gave up on the Realtek drivers. I also tried to install the newer ALSA-driver-1.0.17 but it came up with the same error. Then I installed the alsa-driver-1.0.18rc1 and that worked fine. I have sound again (btw i think it sounds better than when it was with 1.0.16 dirver) but still no HDMI. Now the alsamixergui shows the sound card as ALC885, before it was 882. It's getting closer but it;s still not 889A as it supposed to be :).I think there has to be something that I need to edit in the configuration files or something but I have no idea what else to do.

---

### Post by kaivalagi on 2008-08-30
> **bmwman said:**
> I think there has to be something that I need to edit in the configuration files or something but I have no idea what else to do.

Or maybe the alsa drivers just don't do the job yet...we are talking about a feature that is very new after all...

---

### Post by bmwman on 2008-08-30
Well I thought that's not a new feature at all. This chipset has been out for a long time. That's why I returned the newest one that I bought first with the G43/G45 chipset.

---

### Post by kaivalagi on 2008-08-30
> **bmwman said:**
> Well I thought that's not a new feature at all. This chipset has been out for a long time. That's why I returned the newest one that I bought first with the G43/G45 chipset.

Fair point, but in alsa terms I think it's still relatively new. Looking at the dev changes I can't find any specific mention of Nvidia/Realtek HDMI Audio updates...

Maybe it means nothing, but there is a lot of mention of ATI HDMI Audio but no nvidia...?

Have you tried any of the mythtv orientated forums, they might be a good place to ask questions...

---

### Post by bmwman on 2008-08-30
Well I solved my problem. I went out and bought a whole new amp and connected to it via SPDIF. It really sucks that I had to spend another $500 since that was the whole point of buying this motherboard with HDMI in a first place.

Do what you gotta do I guess.

:)

---

### Post by kaivalagi on 2008-08-31
> **bmwman said:**
> Well I solved my problem. I went out and bought a whole new amp and connected to it via SPDIF. It really sucks that I had to spend another $500 since that was the whole point of buying this motherboard with HDMI in a first place.

Do what you gotta do I guess.

:)

Yeah but a nice home theatre amp really does make the biggest difference for home cinema! :)

---

### Post by xdarkxanarchyx on 2008-09-22
Would running ```
alsaconf
``` help do you think?

---

### Post by kaivalagi on 2008-09-23
> **xdarkxanarchyx said:**
> Would running ```
alsaconf
``` help do you think?

From what bmwman went through I think the limitation is with alsa and nvidia chipsets...

I don't use audio thru HDMI so I can say whether it works or not

bmwman, did you go through the motions with alsaconf etc?

---

### Post by bmwman on 2008-09-23
I have tried anything and everything. I even put the latest ALSA RC and it just doesn't show as it exist. From what I've read Nvidia drivers just do not support audio thru the HDMI in Linux. Something to do with bandwidth or whatever. 

I went out and bought new amp the has optical SPDIF and I'm happy now :). I was just trying to avoid buying a new apm for now but my old analog was just getting too out of date :)

---

### Post by kingmoffa on 2008-11-24
I was wondering if there was anymore news on HDMI + audio for this board. 

Im thinking of getting it , I dont need audio working today - but in a few months time it would be a welcome bonus. 

I need a socket 775 matx board with dvi and/or hdmi with parallel and serial rs232 ports. Any other suggestions?

---

### Post by BluJai on 2008-11-24
Still has a problem for me. I've not been able to resolve it. I have the analog output fed to a 2.1 sound system as a workaround. It is kinda ugly having the extra speakers sitting out in the open beneath the flat-panel (there are no other external audio systems in the room), but I don't have a better solution.

---

### Post by kaivalagi on 2008-12-11
Just read an article on audio over HDMI here: [http://www.phoronix.com/scan.php?page=article&item=linux_hdmi&num=2](http://www.phoronix.com/scan.php?page=article&item=linux_hdmi&num=2)

Not using HDMI based audio myself, not sure whether anything has changed, but thought it was worth mentioning...

---

### Post by bmwman on 2008-12-12
> Support for using HDMI audio through NVIDIA graphics cards was added in the NVIDIA 177.xx driver series Has anyone tested this yet?

I can try it later myself but haven't had a chance to mess with my system lately.

---

### Post by kirlek on 2008-12-28
After a lot of google and some help I now have working HDMI audio on the Gigabyte GA-73-PVM-S2H.

Here is what I did to get it working:

-Fresh install of 8.10

-Install the latest proprietary nvidia drivers. Mine is 177.80

-Download and compile the latest alsa driver. Mine is 1.0.18a. []("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2")[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2)

**Here is the trick, thanks to Nir Tzachar for helping me with this:**
-Add device id (0x10de8001) to snd_hda_preset_nvhdmi table in patch_nvhdmi.c

The end of *alsa-driver-1.0.18a/alsa-kernel/pci/hda/patch_nvhdmi.c* should look something like this:
```

struct hda_codec_preset snd_hda_preset_nvhdmi[] = {
        { .id = 0x10de0002, .name = "NVIDIA MCP78 HDMI", .patch = patch_nvhdmi },
        { .id = 0x10de0007, .name = "NVIDIA MCP7A HDMI", .patch = patch_nvhdmi },
        { .id = 0x10de8001, .name = "NVIDIA HDMI", .patch = patch_nvhdmi },
        {} /* terminator */
};

```

./configure --with-cards=all --with-options=all  (Not sure if we really need any arguments for configure)
make
sudo make install

-Reboot

-Then run aplay -l and you should have a third device:
```
erik@gorm:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

-Run alsamixer -c 0 and unmute IEC958 1

That should be it. Since I'm connecting to my tv I have only tested stereo. But hopefully surround should work to.

If anyone got the surround working please let me know.

---

### Post by spartanmythfan on 2009-01-10
were you able to test 5.1 surround with the info from the last post?  I have Gigabyte motherboard, output hdmi at 760p vi nvidia video card to my denon receiver hdmi, fed to my LCD tv, video is really good, but I really want to get the 5.1 sound working from mythbox.  I have tried the spdif output from the motherboard, but it has never worked no matter what I do in alsamixer or the mythtv audio setup pages.

I would be willing to buy an audio card if that is what it takes, but I tried a while back and never had success.  I really don't want to watch dvd's in stereo sound since I'm spoiled with HD tv and dvd player sound capabilities.

does anybody know of a good audio card that is easily configurable in mythbuntu or whether the previous config works with 5.1?

thanks......

---

### Post by kirlek on 2009-01-12
I am sorry but I don't understand. Did you have working hdmi audio in stereo? 
To get the hdmi audio working try installing the latest alsa and nvidia drivers and you should have all audio working over hdmi.
If you don't have this specific motherboard you should not need any patching before you compile alsa.

I never got any confirmation from that 5.1 is working with the gigabyte ga-73pvm-s2h. But I do know that it works for people with other nvidia cards.

> **spartanmythfan said:**
> were you able to test 5.1 surround with the info from the last post?  I have Gigabyte motherboard, output hdmi at 760p vi nvidia video card to my denon receiver hdmi, fed to my LCD tv, video is really good, but I really want to get the 5.1 sound working from mythbox.  I have tried the spdif output from the motherboard, but it has never worked no matter what I do in alsamixer or the mythtv audio setup pages.

I would be willing to buy an audio card if that is what it takes, but I tried a while back and never had success.  I really don't want to watch dvd's in stereo sound since I'm spoiled with HD tv and dvd player sound capabilities.

does anybody know of a good audio card that is easily configurable in mythbuntu or whether the previous config works with 5.1?

thanks......

---

### Post by phismith on 2009-02-19
Thank you! I have video and audio over hdmi working! Here is what I did:

Updated alsa to 1.0.19 used script here: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

ran aplay -l confirmed hdmi listed as card 0 device 3

created asound.conf with the following:
pcm.!default {

type hw
card 0
device 3
}

ran alsconf (not sure if this did anything)
ran alsamixer -c 0 and unmuted IEC958 1

I hope this helps!!\\:D/

---

### Post by Nicodemus83 on 2009-03-01
Hi 

I've got the same mb and a fresh install of Ubuntu 8.10 and I upgraded the latest Nvidia and alsa driver so I've got the HDMI listed and when I run alsamixer, IEC958 1 is off, so it might sound silly but how can I unmute it?

Could you also tell me the command line for creating asound.conf?

created asound.conf with the following:
pcm.!default {

type hw
card 0
device 3

Thank you
}

---

### Post by Nicodemus83 on 2009-03-01
Oki I unmuted it by pressing M but the volume cannot go up

---

### Post by Nicodemus83 on 2009-03-01
Oki I sorted out by doing again exactly what you've done except the alsaconf

Thanks a lot for your help ;-)

---

### Post by mb36 on 2009-05-22
Thanks for this helpful thread this far! I have the same mobo with 8.10 and mythtv, and after finally plugging it into my TV I run into the hdmi problem. Upgraded alsa to 1.0.20 according to soundcheck's instructions and script. Probably worked because typing in terminal

aplay -l

yields NVIDIA HDMI as the previously absent third item.

But what then? I don't understand how to act on:

"
created asound.conf with the following:
pcm.!default {

type hw
card 0
device 3
}
"
Is this a script? What to do? Grateful for any help.

---

### Post by kirlek on 2009-05-23
Use an texteditor to create/edit the file /etc/asound.conf

For example: sudo nano /etc/asound.conf

Then type/paste in:
pcm.!default {

type hw
card 0
device 3
}

Hope this helps.

---

