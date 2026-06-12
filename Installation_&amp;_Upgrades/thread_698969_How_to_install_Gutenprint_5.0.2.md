---
title: "How to install Gutenprint 5.0.2"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by ImAnOgre on 2008-02-16
Hello,
  First I would like to say thank you to everyone on these forums for all the help you've offered so far, I'm extremely happy with ubuntu so far.

[img]http://digilander.libero.it/le.faccine/faccinea/cartelli/statici/1487.gif[/img]

I have a question though.  I have an Epson cx4400 shared on a windows box and I can find that printer by searching in SAMBA.  Unfortunately Gutenprint 5.0.1 doesn't have the driver I need to print to this printer over my network.

I found that Gutenprint 5.0.2 does have a driver for this printer though, the only problem is since I'm a ubuntu rookie I have no idea how to install Gutenprint 5.0.2.  I've downloaded the gutenprint 5.0.2 tar.bz2 file from sourceforge

 [ LINKY ](http://sourceforge.net/project/showfiles.php?group_id=1537)

and extracted it to my desktop... but I'm at a loss as to what to do from here.

Is there an easy way through the console to install this, and afterwards can I delete the files from my desktop?

Thanks in advance for helping this windows guy move to ubuntu.


[img]http://www.portablegaming.de/images/smilies/thx.gif[/img]

---

### Post by Partyboi2 on 2008-02-16
extract the contents of the tar.bz file and look in the folder its created for a text doc called install, this will explain how to install it.
you will need to install build-essential and probably gcc if you have not already got them installed
```
sudo apt-get install build-essential gcc
```
then change directory so that you are inside the gutenprint folder and then 
```
./configure
```
this may tell you about other packages you need to install. If this goes without error then you can move onto ```
make
```
If no errors there then you can ```
make install
```
[here]("http://monkeyblog.org/ubuntu/installing/#source") is a useful link

---

### Post by ImAnOgre on 2008-02-17
Very informative.  Thank you for the help, I was able to install 5.0.2 with very few problems (I had to use chown to unlock some folders but other then that everything went well.  Do I need to relock those folders?)

Now, second question.  After installing this software, how do I have my printer configuration -- printer via SAMBA point to the new drivers?  Searching my root folder I notice that the new gutenprint folder is in a different location then my 5.0.1 folder.  When searching for printer drivers, I still see the original printers and none of the new ones available in 5.0.2.

Again, thanks for the link, and thanks for the quick help.




[img]http://img320.imageshack.us/img320/3730/a0370fb.gif[/img]

---

### Post by Partyboi2 on 2008-02-17
I can't help you with that but maybe someone else can who knows about printer setup. :)

---

