---
title: "dual boot with win7: no choice to select ubuntu"
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by will_b2 on 2014-05-05
Hello,
I recently installed ubuntu 14.04 on the same hd as an existing win7 os. The installation seems to work, except that there is no option to select ubuntu during boot: the machine boots to windows 7 immediately. 

I ran boot-repair* from a live disc installation, which had no affect on boot options; the data from this operation is at [http://paste.ubuntu.com/7400092/](http://paste.ubuntu.com/7400092/) . Any help in getting a functional dual-boot would be appreciated.


* following the directions of [http://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc](http://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc))

---

### Post by oldfred on 2014-05-05
You have grub installed to the MBR of sda.

But it looks like you have a system with Intel SRT or a small SSD to speed boot. And that may be in control?
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

            Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

---

### Post by will_b2 on 2014-05-05
Thanks for reply oldfred. I was able to achieve successful dual-boot with the following procedure. Though, I can not seem to turn Intel RST back on in windows; this may be outisde the scope of this forum, but I would prefer to continue to use RST in windows if possible. 

For completeness, the procedure I followed is below:

1. Turned off Intel RST in windows, and booted into Ubuntu using live-disc.

2. Followed the dmraid terminal commands as described in post 6-9 in [http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155) 

3. Ran boot-repair following the procedure in [http://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc](http://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc). 

4. Restart demonstrated functional ubuntu/windows choice at startup. 

(5. Cannot seem to turn Intel RST back on in Windows).

Is it clear that I should not be able to use RST ever again? It's probably not a disaster, but it certainly seems like restart times are slower than before. 

Thanks.

---

### Post by oldfred on 2014-05-05
Some more links.
Some have said they could turn it back on.
A few just used SSD for Ubuntu's / (root) and made Ubuntu fast.

       Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

---

### Post by will_b2 on 2014-05-06
Using the Intel RST gui-program in Windows seems straightforward enough. The program says the SSD is available to accelerate the system drive, but after pressing "OK" to nominally begin acceleration no change occurs. According to this tool, the "system is functioning normally" otherwise. I may have to go into Intel's RST program during the boot process, but this is a bit intimidating to me right now, so I will just live with system as is. 

Hopefully I will post a follow up for successfully re-enabling RST before closing the thread...

---

### Post by will_b2 on 2014-05-06
.

---

