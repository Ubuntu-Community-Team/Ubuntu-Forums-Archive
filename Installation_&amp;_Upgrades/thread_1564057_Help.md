---
title: "Help"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by kortni on 2010-08-30
I am trying to install openoffice.org and i am having a bit of trouble. On the directions page it says to 

[LIST=1]
[*]Extract the downloaded archive and open a terminal into the resulting folder.
[*]Browse to the DEBS sub-folder from that directory.
[*]Install OpenOffice.org 3.2 by issuing the following command:sudo dpkg -i --force-overwrite *deb
[*]Install the menu entries by going into the desktop-integration folder:cd desktop-integration
sudo dpkg -i --force-overwrite *deb


I have no idea on how to open a terminal in the resulting folder. 

Can someone please help me?? 

Thanks!!
Kortni
[/LIST]

---

### Post by lechien73 on 2010-08-30
What version of Ubuntu are you running? You can install OpenOffice.org through **Applications > Ubuntu Software Centre**, or **System > Administration > Synaptic Package Manager**.

Just search for **openoffice** and Ubuntu will handle the download of the .deb files, the installation, and the creation of menu items.

---

### Post by dxc on 2010-08-30
we have 10.4 something and i think i found out what we needed  its installed. now she needs to be able to use it for access.  how do we set that up now?

---

### Post by lechien73 on 2010-08-30
If you mean that you need to open Microsoft Access databases, then you will need OpenOffice.org Database. This is not installed as standard, so to install it:

[LIST]
[*]Go to **Applications > Ubuntu Software Centre**
[*]Type **openoffice** into the search box
[*]Click on *OpenOffice.org Database* and select **Install**
[/LIST]
When this is installed, you should be able to open Microsoft Access databases.

---

### Post by dxc on 2010-08-30
ok thank you very much

---

### Post by lechien73 on 2010-08-30
You're welcome. If this issue is fixed, please could you mark it as [SOLVED] using the **Thread Tools** menu at the top right?

---

