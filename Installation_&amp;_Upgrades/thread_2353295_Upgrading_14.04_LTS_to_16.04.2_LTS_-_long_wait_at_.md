---
title: "Upgrading 14.04 LTS to 16.04.2 LTS - long wait at splash screen normal?"
date: 2017-02-20
forum: Installation &amp; Upgrades
---

### Post by sonicwind on 2017-02-20
I'm upgrading my Ubuntu for the very first time ever from 14.04 LTS to 16.04.2 LTS.

It seemed to go normal, and did the restart, but it's been at the Ubuntu splash screen/logo with the five dots for over 30 minutes now.

Is this normal? Is it doing something? The hard drive light is flashing a lot still but I'm beginning to wonder.

I have an Intel i3 (3.3 ghz) - Gateway SX2870.

---

### Post by ubfan1 on 2017-02-20
Try typing ESC to switch to a text screen which may contain errors.

---

### Post by sonicwind on 2017-02-20
Thank you for your help ubfan1. Pressing ESC gave me this error message:

udisksd[26220]: Error performing housekeeping for drive /org/freedesktop/UDisks2/drives/WDC_WD10EZEX_07MNA0_WD_WCC3FRPKY715: Error updating SMART data: Error opening device file /dev/sda: No such device or address (udisks-error-quark,0)

What should I do? Or, if all else fails, how can I get out of this without bricking my hard drive? I was able to use the Live DVD fine before upgrading. Also, I run Ubuntu from my external hard drive (sda).

Thank you so much guys.

---

### Post by sonicwind on 2017-02-20
I should clarify that I tried upgrading by using the software updater in 14.04 LTS, but I'd made a Live 16.04.2 LTS DVD and was able to use it fine yesterday. Also, I have a NTFS data partition on this drive. I didn't think that would matter.

---

### Post by RobGoss on 2017-02-20
> I'm upgrading my Ubuntu for the very first time ever from 14.04 LTS to 16.04.2 LTS.

I would have to recommend doing a fresh installation of 16.04.2 and avoid these issues

My first thought of skipping distributions while trying to upgrade a Linux system would be something will surely go wrong. Waiting **30 minutes** only tells me your system is not responding as it should

I would backup any important data and file, and do a fresh installation of 16.04.2  it's the best way in my option

---

### Post by sonicwind on 2017-02-20
I should have been more clear. My 14.04 LTS system was completely up to date (14.04.5?). I did that, disabled PPA's and made sure I had no proprietary drivers before I attempted the update.

Anyways, I finally realized I could reboot using Alt-PrtSc R E I S U B. After doing so, 16.04 LTS booted!

The only problem I see so far is that any time I type a system command in terminal, it adds this:

N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension.

From Googling, it appears to be a sign that maybe my upgrade is still incomplete, but I did

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

and it's still there.

---

### Post by ubfan1 on 2017-02-20
It's related to an old config file. see [http://askubuntu.com/questions/572976/what-to-do-now-update-just-after-install/573091#573091](http://askubuntu.com/questions/572976/what-to-do-now-update-just-after-install/573091#573091) for an explanation. Look at the contents, and if it's nothing you want to save, you may remove it to stop the notice.  You might want to run fstrim on the ssd, and see what the smartctl -a  report says about your disk.

---

### Post by sonicwind on 2017-02-21
That's a great explanation in that link. Thanks. I'm going to leave it alone since I know what it is now. I looked at both files and there's not much difference.

I ran a SMART test on my HD and it says it's all good. Everything seems to be running fine, so I'm going to mark this solved.

Thanks for your help.

---

