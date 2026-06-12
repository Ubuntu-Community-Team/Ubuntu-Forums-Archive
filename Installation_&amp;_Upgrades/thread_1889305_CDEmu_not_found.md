---
title: "CDEmu not found"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by Lordestabia on 2011-12-01
I followed the instructions given to add CDEmu to my repository by executing the following.
**sudo add-apt-repository ppa:cdemu/ppa**

The Response was as follows
[INDENT]*You are about to add the following PPA to your system:*
* PPA for CDEmu*
* Unofficial CDEmu packages*

*Ubuntu 11.04 - Natty series (support discontinued)*
*Ubuntu 11.10 - Oneiric series*

*IMPORTANT: I highly recommend you read the installation and usage notes:*
*[http://cdemu.org/debian/](http://cdemu.org/debian/)*

*If you find any packaging bugs you can report them by clicking on the "bugs" button above. Just make sure the bug is assigned to the cdemu project. For any other kind of bug please report the bug to the sourceforge bug tracker.*
* More info: [https://launchpad.net/~cdemu/+archive/ppa](https://launchpad.net/~cdemu/+archive/ppa)*
*Press [ENTER] to continue or ctrl-c to cancel adding it*

*Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.uUvJbrhsZ8 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv AFDF4CC6A4F32AA9395FAE8F423A2125D782A00F*
*gpg: requesting key D782A00F from hkp server keyserver.ubuntu.com*
*gpg: key D782A00F: public key "Launchpad PPA for CDEmu" imported*
*gpg: no ultimately trusted keys found*
*gpg: Total number processed: 1*
*gpg:               imported: 1  (RSA: 1)*
[/INDENT]I then executed the following as directed
**sudo apt-get update**

After that was complete, I tried installing cdemu, **sudo apt-get install cdemu** and I get this.
[INDENT]*Reading package lists... Done*
*Building dependency tree       *
*Reading state information... Done*
*E: Unable to locate package cdemu*
[/INDENT]What am I doing wrong? I've followed the instructions to the letter.
:confused:

---

### Post by Goa'uld on 2011-12-13
> **Lordestabia said:**
> 
After that was complete, I tried installing cdemu, **sudo apt-get install cdemu** and I get this. <snip> What am I doing wrong? I've followed the instructions to the letter.
:confused:

so far so good.

try "sudo apt-get install cdemu-client gcdemu" instead. that installs the client applications and pulls the rest also.

---

### Post by ossi1970 on 2012-03-21
Worked for me, thank you!:guitar:

---

### Post by teoman99 on 2012-08-01
Re: How to install cdemu..
I want to explain my experience with ubuntu 11.10 or higher in cdemu installation

open software installation center in ubuntu 11.10
in top menu ----> edit ----> software resources ----> enter password
a window is opened for software sources
here click     Third-party software    menu then add button

in the opened window enter ( ppa:cdemu/ppa ) without parenthesis

click add resource button

in command line sudo apt-get update

repository is updated.

in software installation center search for cdemu

packages cdemu-client    gcdemu   extra  extra come
install them
for mounting ----> open the iso file in nautilus ---> right click ---->open with cdemu client

a new nautilus window is opened -----> there you see your virtual cd

You can Mount 2 CD /DVD drives at once. 

     CDemu  supports following formats:-

    .nrg format,
    .cdi format,
    .ccd/.sub/.img,
    .cue/.bin format,
    .iso format,
    .toc format,
    .b6t format,
    .mds format,
    .cif format,
    .c2d format,
    .daa format.
    .toc format.

---

