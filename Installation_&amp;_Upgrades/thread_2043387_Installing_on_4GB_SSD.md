---
title: "Installing on 4GB SSD"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by CPTrueTech on 2012-08-16
I am trying to install the latest version of Lubuntu (12.04) on a Dell Mini (Model # PP39S) and am having problems regarding drive space.

The netbook contains a 4GB SSD, but according to the installer, I need a minimum of 4.4GB, and I can't continue from there. I did some research and it seems this check is a bit higher then necessary. I also noticed that for the 11.04 version, someone produced instructions on how to manually edit the disk size limit by changing a variable in a text file. It seems that this method no longer applies in the 12.04 version.

Can anyone help me get this installed? Thanks so much in advance.

---

### Post by Rex Bouwense on 2012-08-16
If one can install Lubuntu on a 4 Gb flash drive, one can certainly install it on an 4 GB SSD.  See this site for guidance,
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303).

---

### Post by CPTrueTech on 2012-08-16
Thanks so much for responding. However, it seems like that solution will not work. As soon as I click the button to begin the installation procedure, a window pops up with the minimum requirements:

- Minimum of 4.4 GB of HDD space
- Is plugged into a power source
- connected to internet

The bottom two have a green check mark, the HDD space has a grey X. The "Continue" button on this page is disabled, and I cannot go further.

There must be a way to manually up the HDD limit as with 11.04. I don't see why a distro should need a whopping 4GB of space just for install.

---

### Post by Jt00 on 2012-08-16
You could try one of the alternate installs from [here]("http://www.ubuntu.com/download/desktop/alternative-downloads").
With only 4GB of space on the computer, you may just want to buy a large capacity USB stick and run Ubuntu from that. That way you could save everything with much more space. I know Officemax and Office Depot sell USB sticks for about $20-30 for 16-32 GB. You could also buy online if you don't have one of those near you.

---

### Post by CPTrueTech on 2012-08-16
If I had things my way, I wouldn't be running on a 4GB SSD in the first place. This is actually for a client, and I have to get a full install on this netbook. I know for a fact that there are Linux distros fully capable of running on so little, but I specifically wanted an Ubuntu derivative for the sake of ease-of-use.

Is it relatively trivial to get the LXDE desktop and other basic features installed via the "alternative" source? Are there any guides on doing so?

Again, thanks for the help and advice, it's appreciated

---

### Post by oldfred on 2012-08-16
You can install the minimal:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Then from the left side panel choose the pure Lubuntu and install those apps. If you add the full Ubuntu you will be too large. And an install in only 4GB will require regular maintenance to remove logs, history etc so it does not fill up.

---

### Post by C.S.Cameron on 2012-08-16
On my 4GB EEE, I did a persistent install, which works ok.
I recall installing to a flash drive then dding to the hard drive.

---

### Post by C.S.Cameron on 2012-08-16
On my 4GB EEE, I did a persistent install, using UNetbootin, which works ok.
I recall installing to a flash drive then dding to the hard drive.

---

### Post by Khal1d on 2012-08-16
I've encountered something similar to your problem, and was trying to find a work around for it. 

However!

What I found out was it was easier to just re-partition the drive and install it into a 5GB drive, or 10 in my case. (I was going over board due to frustration! :( )

If I may ask...why not just do that? Allocate more space?

You could backup the data and do it yourself, if the Laptop is in your possession. Be sure to tell him/her before you do it though! :lolflag:

Just a thought...

---

### Post by mastablasta on 2012-08-17
> **Khal1d said:**
> If I may ask...why not just do that? Allocate more space?

 
because the disk is not bigger than 4 GB.
 
anyway minimal iso seems to be the way to go. additionally you might want to try something else such as Bodhi linux (Ubuntu based)
>  
The minimum requirements to run Bodhi Linux are only: 300+MHz CPU, 128MB RAM, and 2.5GB hard drive space!
or something smaller like Anti-X.
 
however if you plan on having some heavier applicaitons you would need at least 8GB and even that won't leave much space for data.

---

### Post by CPTrueTech on 2012-08-19
> **oldfred said:**
> You can install the minimal:
anyway minimal iso seems to be the way to go. additionally you might want to try something else such as Bodhi linux (Ubuntu based)
or something smaller like Anti-X.
 
however if you plan on having some heavier applicaitons you would need at least 8GB and even that won't leave much space for data.
Thank you for the recommendation, I will try it out. Seems like the easiest solution to me, since I'm not married to any particular distro.

I am assuming that if the person ran "heavy applications" they would be using something other then a netbook. I imagine its for browsing the web and not much else.

---

### Post by TenPlus1 on 2012-08-19
when installing Lubuntu to a 4gb partition or flash device remember and remove the swap partition so that all files will fit on the device...  If you are booting from USB flash drive this will also speed up Lubuntu considerably...

---

