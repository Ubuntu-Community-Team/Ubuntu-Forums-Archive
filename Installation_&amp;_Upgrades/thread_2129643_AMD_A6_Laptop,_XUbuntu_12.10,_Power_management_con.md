---
title: "AMD A6 Laptop, XUbuntu 12.10, Power management config / tuning - advice ?"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by mistertdc on 2013-03-26
Hi,

I've recently got a small "ultrabook-style" samsung laptop ("series 5" with AMD a6 Vision APU type of CPU:Graphics - A6 4455M CPU, it is a 2.1ghz dual core CPU) which had Win7 pre-installed.  Battery life is just over 3.5 hours (basic wifi / internet browsing / web page use, brightness mid-level for screen, using pre-configured 'samsung eco mode' power profile in Win7).

I installed Xubuntu 12.10 / 64bit (I've got 6 gb ram on this thing hence 64bit OS pick) - (dual booting, kept windows around for now) - and everything installs very smoothly - all hardware (sound:video:network:wifi) works out of the box without issue.  But my battery life is pretty horrible - 1.5 hours if I am lucky.  I note that the laptop physically runs hotter, the fans are louder, and I get the feeling power management / resource throttling is simply not working as well.

I installed "Jupiter" power management tools; made sure cpufreq is installed (I'm not convinced it is doing much); and so far .. no real change that I can see.  According to /proc/cpuinfo - the mhz is being dropped from high (2100mhz) to low (1300mhz) after a while / when things are not 'super busy' on the laptop.

Google searches find about a million different articles and suggestions, spanning approximately 10 years; and a bunch of various ubuntu versions.  I understand that the more recent ubuntu is meant to be better at this than earlier ones but .. I am uncertain, maybe there is something required to configure 'laptop mode' which is not immediately obvious.

Are there any moderately straightforward steps that can be taken to address this?  I'm happy to install, customize - as required - but I simply am having trouble finding what else can be done; and this seems like such a major issue that I'm hoping there are some pointers on how to make AMD APU based laptops work a bit better for power consumption.

(As a side note: "Suspend" seems to work poorly - also maybe power related - in the sense, I can suspend the machine, but when it 'wakes up' - I just get a blank screen and have to give up and power off hard eventually .. then reboot, and so forth. This kind of stinks, also, but is slightly less concern out of the gate than the battery life issue).

Any comments / thoughts / pointers are greatly appreciated.

Many thanks!


Tim

---

### Post by Toz on 2013-03-26
Hello and welcome to the forums.

Have you installed the proprietary AMD graphics drivers? You should be able to find them in the Software Centre under Edit->Sources->Additional Drivers tab.

Also feel free to post the contents of your dmesg log file for review. From a terminal window, run:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

### Post by mistertdc on 2013-03-27
Hi, Many (!) thanks for the response. I had not enabled the AMD (non-open) drivers - didn't really know where-how to do this without your pointer.

Applied that change, rebooted, catalyst control settings are now available..

As per your request, my dmesg output is now at,  [http://paste.ubuntu.com/5653927/](http://paste.ubuntu.com/5653927/)

Many thanks,

Tim

---

### Post by Toz on 2013-03-27
Does adding these drivers improve your battery life? Have a look at [this wiki article]("https://help.ubuntu.com/community/PowerManagement/ReducedPower") (especially related to the powertop tool) for more tips on improving battery life.

---

### Post by mistertdc on 2013-05-07
Hi, a quick followup: I did a bit more testing; for 'fun' tried a few different ubuntu and related distros.  Enpoint,

- ATI official (non-open) drivers helped significantly (approx doubled baseline battery life, from ~1.25 to ~2.5 hours)
- adding "laptop-mode-tools" helped a bit more (significantly - extra 30min? approx)
So now in general I'm getting good battery life .. in Ubuntu..
- adding "powertop" was good to quickly check "watts power discharge rate" when running on battery; and also to see how "good" or "bad" power-save features were for various aspects of the hardware...

I still have the impression the laptop runs warmer, in ubuntu, when cabled to AC power -- than it does similarly with Win7 running / with AC power present; I am not certain if there is a way to encourage more power saving when the laptop feels no 'pressure' to conserve.

But in general - this is major improvement so I'm happy.


Tim

---

