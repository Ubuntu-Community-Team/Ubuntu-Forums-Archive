---
title: "Upgrader/Synaptic doesn't work"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by racsw on 2006-06-04
Hi,
I'm wrting this on 6.06 on a 3.4 GHz machine and it's running ok.
For some reason, my Upgrade notification brings up three Upgrades to be downloaded and installed, two of which are to do with the automatic upgrader itself.
I tell it to go ahead, and it fails on all three.

Then I go to the Synaptic Package Manager, and upgrade my repositories using the regular GUI.
When I click on Reload, it tries to download a bunch of indexes, but then fails with errors on every repository, and it tells me it couldn't connect.
Yet my network connection is working fine, I'm getting my email, and FireFox is working great, so there's nothing wrong with my network connection.

Here's the messages for the downloader:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...0.1.33_all.deb](http://us.archive.ubuntu.com/ubuntu/...0.1.33_all.deb)
Connection failed [IP: 85.133.25.8 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...0.1.33_all.deb](http://us.archive.ubuntu.com/ubuntu/...0.1.33_all.deb)
Connection failed [IP: 85.133.25.8 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...untu6_i386.deb](http://us.archive.ubuntu.com/ubuntu/...untu6_i386.deb)
Connection failed [IP: 85.133.25.8 80]
racsw is online now   	Edit/Delete Message

How do I get these fixed?

Regards,
Robert

---

### Post by rcarring on 2006-06-04
Sometimes the repos sites become unavailable. There is nothing wrong with your  connection from what you say.

If you can identify the names of the packages you may be able to download them from packages.ubuntu.com and manually install them by double-clicking on the deb file in Nautilus. Create a launcher that has gksudo nautilus as the command line, and this will give you Nautilus running as root.

---

### Post by racsw on 2006-06-06
Hi,
  I saw this as two different problems myself, but the main point is, how do I fix the upgrader?

Secondly, I cannot select any of the Universe selections either, I get similar errors.
All this used to work fine with 5.10, but none of it works with 6.06.

Thanks,
Robert

---

