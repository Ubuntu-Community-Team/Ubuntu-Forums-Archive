---
title: "Upgrading to 11.10 from 11.04 was fine until interrupted, and now it's slow etc"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by djpurity on 2011-10-19
I basically was doing okay with my ubuntu amd 64-bit upgrade on my Acer 5251-1805 with 62-bit AMD 2.2 GHz V120 processor, 3 GB DDR3 RAM, ATI Mobility Radeon HD4250 Graphics w up to 1.4GB Hypermemory, a 500 GB new WD harddrive I installed and replaced the original one that came with Windows 7 on it, and that's about it for stats.

I plugged directly in and was wirelessly connected to my router for like 2 days straight downloading this upgrade and installing. Everything was fine until I answered one question as something I wanted more information on. Then it started to ask technical questions and things that I didn't really know, and it was going on and on, and I wanted to just cancel out of this question troubleshooter or so I thought it was, but it cancelled the rest of the Ubuntu upgrade!!

I went immediately to upgrade manager or update manager (I get them confused for some reason) to attempt to try to finish, and it did have a place at the top that linked to updating the system, and I clicked it, but it did not go back to the snazzy upgrade screen that had the 4-5 basic steps (check system, download, do something with repositories, install upgrade, remove and clean up, and then reboot. Or something like that). It went through some things on the terminal, but it didn't do any cleaning up phase. Or rebooting. But I did have to reboot at one point to finish the update or some application.


My system has been slow, sluggish, it crashes, and it is missing some icons and features. I've tried running update manager many times and it says I have no updates no matter how many times I check!

 I also think at one point it told me to reboot to finish the installation of something, or perhaps for the whole system to finish. I was on wirelessly and directly thru ethernet to router, so I wasn't sure which way it was getting the data, but I wanted to move my computer so I unplugged its ethernet. Then at startup it gave a message network failure to find, giving it another 60 seconds then aborting, so I rushed to replug it back in directly, but I guess I was too sloowwwwwww. Or something because it never found it and started up, and things have sucked for me ever since.

I have found the sound icon at the top navigator bar to be gone, and I had to manually unmute it from not running alsa or anything, but going to system settings and just going to sound and turning it off from the HDMI output to the onboard sound output thru the speakers. I usually use the HDMI output to hook my laptop up to a nice HDTV via HDMI cable and then close my laptop and use the tv as my monitor and my laptop as my "desktop" and then plug an external keyboard in, tuck the laptop away, and use a wireless mouse. It's nice to watch Internet tv or whatever on, hulu, etc. So I could see that mistake. But it used to be easily accessible, and I am sure there are other little things like that maybe would have been fixed had the installation gone completely through and cleaned itself up.

Now how can I get a fresh clean install? I was talking to this guy who loves Debian and that's his O/S and he talks about that and various forms of Linux that use rolling updates so that no matter what state you had it in, it would get to the latest state and be up to date without these "upgrades" or installations to the latest "update" or "version" .... and I see the positive in that.

But I do not like how slow it is and I do not like a lot of thinsg about it, but mostly, it bothers me that I don't feel that I got a full installation, and that most of the problems I have are from that. Can I roll back and then start all over and do the update again? I am downloading a fresh 64-bit installtion disk of the 11.10 version, so I thought if anything, I'd have the iso around to mount or to burn so i CAN finish this upgrade the right way, if only someone could help me out...

And my lack of paying better attention is due to it being super early morning and I am a late sleeper and I just was checking on the status of the update because it took all of the half day before to download and go through most of the updates and all that, and every once in a while there would be a question screen wanting a response, or a return key pressed, so I would check it, not really paying close attention. So I cannot say where it went wrong and I cancelled out of it but somehow cancelled the entire installation. And I don't know if the wireless and ethernet thing also had an effect. All I know is what I can give you with some terminal command that would reveal the info you need.

Anyone help me out here to smooth this out and really get back to the root of things? And I know it turned off a lot of the 3rd party repositories and last update did that and didn't turn them back on so there were some issues even after a good clean install as a result, but I turned them on and it was easy: turn them all back on. But now, I had some turned off from 11.04 and others from 10.10 and I don't know if they all need to be turned on or what. But I had dozens it seemed when I don't recall even having that many repositories before the install anyway of 3rd parties...


Okay I think that's all the info I can give.... I await some beaner to help me, and that is not a carlos mencia joke either, as sad as it is to even invoke that one's name... <g>

---

### Post by zvacet on 2011-10-21
Turn off all third party repos until you fix your system.If upgrade is not complete try this command

```
sudo apt-get -f install
```

If you ger any errors post them here.

Ubuntu does not work as rolling release,and if I understand correctly your friend use Aptsoid.You can find more rolling releases if you want to try them.Maybe you can try PClinux of Sabayon.

---

