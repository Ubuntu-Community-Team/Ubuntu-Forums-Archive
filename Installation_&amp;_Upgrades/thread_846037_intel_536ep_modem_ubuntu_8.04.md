---
title: "intel 536ep modem ubuntu 8.04"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by somi38 on 2008-07-01
how can i install intel 536ep modem driver on ubuntu 8.04

---

### Post by dstew on 2008-07-01
It might be difficult to get that modem working. Here is a link to a [generic Linux driver source tarball]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=6497&strOSs=39&OSFullName=Linux*&lang=eng"). You will have to compile this driver yourself. The Readme says that it has Debian support, but it looks like it really leans heavily toward Red Hat and SuSe.

To compile the driver, you will first need to install the **build-essential** and **linux-headers** packages, using Synaptic (System --> Administration --> Synaptic). You will need the linux-headers package that exactly matches the kernel you are currently using. To find your kernel version, open a Terminal window (Applications --> Accessories --> Terminal) and enter the command```
uname -r
```

After you have installed these packages, download the driver file, which ends in tar.gz. Double-click the downloaded file to extract it. It should create a folder with the name intel-536EP-2.56.76.0. Once you have created that folder, you need to use the terminal to compile the driver. Use the **cd** command in the terminal to enter the folder. If the folder is on the desktop, do```
cd ~/Desktop/intel-536EP-2.56.76.0
```If the folder is in your home folder, do the same, but leave out /Desktop.

Once in the folder, open the Readme file for directions. Instead of becoming root, just preface the commands with **sudo**.

If you get the driver to compile, you may need to follow the install-by-hand instructions in the Readme, Installation section near the bottom, to get the driver functioning, if **make install** fails.

---

### Post by somi38 on 2008-07-03
how can i install build-essential and linux-headers packages



and sen me please details of intel536ep modem package

---

### Post by Partyboi2 on 2008-07-03
Do you have internet access currently with ubuntu box that you are trying to get the modem to work?

---

