---
title: "Lubuntu 10.10 and 11.04 installation help"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by njhomeowner on 2011-08-06
Hi,

I just started experimenting with Lubuntu as we use older equipment.  I downloaded the 11.04 iso and after burning it when I try to boot from the CD it hangs at what looks like a GRUB boot prompt.  I tried this in several machines with no change.

I then downloaded and successfully installed Lubuntu 10.10, and attempted to run the distribution upgrade to 11.04.  During the upgrade many packages failed to install (close to 50 at least).  Once the upgrade was complete the computer hung on restart.

Any suggestions on either of these items - I really would prefer to be using Lubuntu 11.04.

Thanks

---

### Post by oldfred on 2011-08-06
How much RAM does system have? I think you need 512MB for Ubuntu to work.

If a boot issue this may help:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by JC Cheloven on 2011-08-06
Hi, as it fails in several pc's, I'd say that you have the typical bad CD problem. 

Please check the md5sum of the downloaded file, burn the CD at low speed, etc. Devil is in the details. That kind of problem occurs more frequently that one would think.

Note: LUbuntu [should run on 128Mb ram]("https://wiki.ubuntu.com/Lubuntu"), this shouldn't be the problem.

---

