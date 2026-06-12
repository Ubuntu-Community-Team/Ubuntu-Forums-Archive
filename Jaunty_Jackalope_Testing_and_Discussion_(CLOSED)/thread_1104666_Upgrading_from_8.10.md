---
title: "Upgrading from 8.10"
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by alphacrucis2 on 2009-03-23
I decided to jump in an upgrade my test Intrepid machine to Jaunty.
I did update-manager -d and it displayed the option to do the upgrade. It wanted to download 1393 packages. It ran through the downloads fairly quickly but it seems to have stalled on file 1356 of 1393. It has been sitting on that file for over an hour now. Not sure if I should cancel it and try again or just be patient and leave it. Any suggestions.

---

### Post by alphacrucis2 on 2009-03-24
> **alphacrucis2 said:**
> I decided to jump in an upgrade my test Intrepid machine to Jaunty.
I did update-manager -d and it displayed the option to do the upgrade. It wanted to download 1393 packages. It ran through the downloads fairly quickly but it seems to have stalled on file 1356 of 1393. It has been sitting on that file for over an hour now. Not sure if I should cancel it and try again or just be patient and leave it. Any suggestions.

After a couple of hours I gave up and restarted update-manager. It tried to continue from the package it was stuck on. Still stuck. I gave up and have downloaded the alpha 6 iso. Will try upgrading from that tomorrow.

---

### Post by DarkReaper79 on 2009-03-24
I had the same problem. I tried to update, it failed. Couldnt recover Interpid, reinstalled it, failed to recover it. Downloaded the Jaunty iso, and it worked. Thankfully I had backed up my stuff!

---

### Post by jerrylamos on 2009-03-24
> **alphacrucis2 said:**
> I decided to jump in an upgrade my test Intrepid machine to Jaunty.
I did update-manager -d and it displayed the option to do the upgrade. It wanted to download 1393 packages. It ran through the downloads fairly quickly but it seems to have stalled on file 1356 of 1393. It has been sitting on that file for over an hour now. Not sure if I should cancel it and try again or just be patient and leave it. Any suggestions.

One suggestion is to boot in recovery mode, then select "fix broken packages".  That's worked for me a number of times.

Do note I run at least two boot images so if one gets screwed up by updates I can still run from the other.  Also I have a 3rd partition where documents & handy programs are stored, accessing them through "Places > Home Folder > name of partition".  Sharing a home partition has failed for me if it is shared between two different levels of Ubuntu since there are a lot of hidden files in home preceded by a ".".

Jerry

---

### Post by andrewabc on 2009-03-24
> **alphacrucis2 said:**
> After a couple of hours I gave up and restarted update-manager. It tried to continue from the package it was stuck on. Still stuck. I gave up and have downloaded the alpha 6 iso. Will try upgrading from that tomorrow.

Wait until Thursday/Friday and get the beta. Less chance of stuff breaking.

But do try the alpha 6 live cd to make sure everything works on that.

---

### Post by alphacrucis2 on 2009-03-25
Just reporting that using the iso sorted out the problem. I have /home on a separate partition so there isn't too much risk. I will wait till the official release before upgrading my main machine.

---

