---
title: "Failed to download repository information"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by CMac12 on 2013-10-19
The software updater checks for updates and then says that there is no internet connection, but there must be because I'm using the internet to post this?

---

### Post by heir4c on 2013-10-19
Try it again and wait a while. Here in 13.10 I have a message to, but after a while he opens the list with updates. (a small bug?) Or try a different server to update and upgrade.

---

### Post by grahammechanical on 2013-10-19
Does it say there is no internet connection? Or does it say it cannot download repository information - check the internet connection? Can you not click continue? That sometimes over comes the blockage. It sounds to me that you may have repositories that are PPAs (Personal Package Archives) that may no longer be maintained. You may need to remove those PPAs or stop Update Manager from attempting to connect to them to find out if there is any package in the archive that has been upgraded by the developer.

Regards.

---

### Post by john-john-42 on 2013-11-10
Dear Grahammechanical,
I think I am having the issue that you mention here - these are the details of my issue which sound similar to those above:

E:GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

Does that sound right? I'm currently using Ubuntu 12.04, and I've tried changing the server that provides the updates download.

Cheers
John

---

### Post by philinux on 2013-11-10
Remove medibuntu sources. They are now defunct.

---

### Post by john-john-42 on 2013-11-10
I assume you mean by unchecking it in the update preferences? If so -brilliant - I did that and it worked, thanks!

---

### Post by philinux on 2013-11-10
Personally I deleted them. Glad you're sorted now.

---

