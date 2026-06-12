---
title: "[ubuntu 13.10] Suspend/resume scripts not executing (systemd)"
date: 2014-03-22
forum: Installation &amp; Upgrades
---

### Post by David Woodward on 2014-03-22
I have an Acer C720 Chromebook that I've loaded ubuntu 13.10 onto... kind of.  Since it's limited in space I took this opportunity to learn how to install a very minimal installation and I think I may have trimmed a little too much off.

The problem is that scripts dropped into /usr/lib/systemd/system-sleep are not executing on sleep/resume.

I found another person having a similar problem which they resolved by installing pm-utils and then placing the pm-utils equivalent to their script in /etc/pm/sleep.d and I was able to get that to work.  However, I'd still like to know what I missed installing for the (seemingly more common/standard) systemd method not to work.

I've checked to ensure that systemd-services is installed, the scripts were marked as executable, and they run manually without error and the exact same script works under the pm-utils (after changing "pre/post" args to "suspend/resume").  So, I really don't think it's something I'm doing wrong in regard to the script setup.  I think there must be some component that it depends on that I didn't install.

For your refrence, here are the commands I used to install my minimal ubuntu desktop environment on top of my minimal command line install.

```
[COLOR=#000000][FONT=Arial]sudo apt-key update[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt-get install software-properties-common[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt-get install wget apt-transport-https[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt-key update[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]sudo apt-add-repository 'deb https://dl.google.com/linux/chrome/deb/ stable main'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt-key update[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]sudo apt-get install --no-install-recommends ubuntu-desktop[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt-key update[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]sudo apt-get install gparted samba gnome-control-center-unity unity-scope-home google-chrome-stable indicator-application indicator-appmenu indicator-bluetooth indicator-messages indicator-power indicator-printers indicator-session indicator-sound indicator-sync indicator-datetime indicator-power indicator-session ttf-ubuntu-font-family unity-lens-applications unity-lens-files network-manager-gnome synaptic gnome-terminal plymouth-theme-ubuntu-logo activity-log-manager pm-utils gcc make linux-headers-$(uname -r)[/FONT][/COLOR]
```

And then of course I had to recomplile the kernel to include the funky touchpad drivers (which seem to be more sensative to grounding issues than whatever the actual ChromeOS is using - but that's another story)

```
[COLOR=#000000][FONT=Arial]mykern=`ls /boot/vmlinuz-* | grep -oP "[0-9].*" | sort -rV | head -1`
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]wget http://goo.gl/kz917j[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo bash kz917j $mykern[/FONT][/COLOR]
```


Thanks in advance for your help.

(Hopefully this hasn't already been covered.  I did search the forums before posting, but I couldn't find this specific issue mentioned anywhere)

---

### Post by TheFu on 2014-03-22
So, I picked up the C720 a last week too - never intending to run ChomeOS.
Loaded 13.10 on it, purged Unity, loaded LXDE and started configuring it.  No need to build touchpad drivers. Seems fixed with just a few settings.  I did find a link over at #! which helps to setup everything to be relatively comfortable.

I'm also fighting with the suspend and the **fracking power button**.  Whoever designed that location needs to be killed, slowly, over 50 yrs of their life. Toenails, waterboarding, clipped fingers, acid in the eyes ... they deserve it all.  Today, I've already pressed the DEL key 5 times subconsciously (which is hte power key). Yesterday, it was hit about 30 times - powering off every time.  The day before it was more ... almost threw it off the 30th floor of a bldg here over that.

Anyway - I think there are links to the links on my blog: [http://blog.jdpfu.com/2014/03/12/ubuntu-on-acer-c720-chromebooks](http://blog.jdpfu.com/2014/03/12/ubuntu-on-acer-c720-chromebooks)  Besides the power key quagmire, I'm loving this netbook!  Oh - and this: [https://github.com/liangcj/AcerC720CrunchBang](https://github.com/liangcj/AcerC720CrunchBang)

---

