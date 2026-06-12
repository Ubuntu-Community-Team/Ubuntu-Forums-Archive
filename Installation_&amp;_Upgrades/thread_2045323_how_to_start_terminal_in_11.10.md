---
title: "how to start terminal in 11.10"
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by argo1 on 2012-08-21
I need to use terminal to install hplip for a laserjet  but I forget how to get terminal to work the first time from install. I opened terminal...typed in su...password...authentication failure comes up. In older versions I went to users and groups and did...can't remember that part to get terminal to work...need help. Also how to get that hp laserjet to work...says it needs drivers.

---

### Post by coffeecat on 2012-08-21
> **argo1 said:**
> I opened terminal...typed in su...password...authentication failure comes up.

In Ubuntu, use sudo for temporary elevation to root privileges. See here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by darkod on 2012-08-21
During the printer install/add ubuntu can usually locate the correct driver, download and install it. At least that's what it did with my Epson SX510W multifunction.

Did it try to download a driver for you?

---

### Post by argo1 on 2012-08-21
Did not try "sudo" just su.  When I tried to locate drivers from ones available during "add" this one,,,HP LaserJet Professional M1214nfh Multifunction Printer...was not listed.

---

### Post by coffeecat on 2012-08-21
> **argo1 said:**
> HP LaserJet Professional M1214nfh Multifunction Printer

This model is supported out of the box in Ubuntu 12.04. Double-check that it is not already supported in 11.10. I'll reboot into 11.10 later and check anyway.

---

### Post by darkod on 2012-08-21
OK. So, is this driver a package you downloaded from the manufacturer, or you are talking about some package from the repositories?

Packages in the repositories are installed with:
sudo apt-get install <package name>

On the other hand, downloaded software/programs/drivers usually need to be unpacked (they come compressed), and there will usually be a readme.txt file with instructions how to start the install. For example there might be install.sh file to run, in that case open terminal, open the directory where the extracted files are, and try something like:
sudo ./install.sh

As I said, the readme should have info how to do it.

---

### Post by darkod on 2012-08-21
> **coffeecat said:**
> This model is supported out of the box in Ubuntu 12.04. Double-check that it is not already supported in 11.10. I'll reboot into 11.10 later and check anyway.

If it's supported in 11.10 wouldn't it simply install all it needs?

To the OP, are you sure the printer is not installed?

---

### Post by coffeecat on 2012-08-21
> **argo1 said:**
> HP LaserJet Professional M1214nfh Multifunction Printer...was not listed.

> **coffeecat said:**
> This model is supported out of the box in Ubuntu 12.04. Double-check that it is not already supported in 11.10. I'll reboot into 11.10 later and check anyway.

I'm now posting from 11.10. The driver for this model of HP printer is already included in a default installation of 11.10. You do not need to install the downloaded package. What steps did you take to configure 11.10 with this printer? This is not clear from your post.

If your system does not autodetect and setup your printer, open the Printing utility and click on "add". Type "http://" (without the quotes) in the "Enter device URI" field and click on Forward. Make sure "select printer from database" is ticked, select HP from the list and then click on Forward. Your model is about halfway down the very long list. Select that and click on Forward. Click on Apply on the next page and your system should then be set up for your printer.

---

### Post by coffeecat on 2012-08-21
> **darkod said:**
> If it's supported in 11.10 wouldn't it simply install all it needs?

Not necessarily. I've experienced the system failing to autodetect and set up a supported printer, in which case I had to do it manually as per my previous post.

---

### Post by darkod on 2012-08-21
> **coffeecat said:**
> Not necessarily. I've experienced the system failing to autodetect and set up a supported printer, in which case I had to do it manually as per my previous post.

I meant if using Add and selecting the correct model. I never trust cable auto detect or similar if that's how people mainly install these days. :)

You are right, we are missing details how the OP tried to install it. I was going under the assumption he used the Add option and selecting the model, but now I see that assumption might be wrong.

Maybe he only expected auto detect of some kind.

---

### Post by coffeecat on 2012-08-21
> **darkod said:**
> I never trust cable auto detect or similar if that's how people mainly install these days. :)

I know what you mean! :) I find that either there's a popup seconds after I plug in a supported printer telling me it's been auto-installed, or nothing at all. In which case I install it manually with the "add" button in the Printing utility.

---

### Post by argo1 on 2012-08-22
Made a mistake with number of printer as it was at the office. It is a laserjetM1217nfwMFP and I can't find the list of printers in 11.10...can't find "add printer for that matter.

---

### Post by coffeecat on 2012-08-22
> **argo1 said:**
> Made a mistake with number of printer as it was at the office. It is a laserjetM1217nfwMFP and I can't find the list of printers in 11.10...can't find "add printer for that matter.

Follow the directions I posted in post #8, last paragraph. To open the printing configuration utility, open the dash by tapping the super (Windows) key, type "print" and select "Printing". Then follow those directions. The M1217nfwMFP is listed in 12.04 - I'd be surprised if it isn't listed in 11.10.

---

### Post by argo1 on 2012-08-28
Well...made some headway and then stopped. Installed hplip (thanks for info on accessing terminal) 3.12.6 ...ran but had switched out to a hp 1212 laserjet. It ran the test page...eureka. Took PC and printer to office, hooked everything up and no way in this world would it print. Says it's ready to print but nothing. Reinstalled hplip got the extra download item from HP...still no print. 
Is there a plug and play laserjet of whatever brand you could recommend other than this as it is driving me nuts. 
My Canon MP 210 just plugged and played but its no good for all the office work because of the limited ink

---

### Post by argo1 on 2012-08-28
Should have also said I updated to ubuntu 12 still couldn't find 1217nfw though so put my 1212 laserjet (which is listed) in its place that is connected with the only windows computer we have in all 4 complexes

---

