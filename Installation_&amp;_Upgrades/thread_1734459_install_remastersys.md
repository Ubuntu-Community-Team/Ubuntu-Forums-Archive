---
title: "install remastersys"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by akbarg64 on 2011-04-20
Hi.I want to install software remastersys. But I am faced with this error  Unable to locate package remastersys
. I'll act as follows:(
sudo nano /etc/apt/sources.list
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

sudo apt-get update
sudo apt-get install remastersys


please help me.thanks.

---

### Post by akbarg64 on 2011-04-21
please help me](*,)

---

### Post by ~Plue on 2011-04-21
did you save the file after adding the repository line? post the contents of the file; (run the following from a terminal)
```
gksu gedit /etc/apt/sources.list
```

---

### Post by akbarg64 on 2011-04-21
Thanks.Yes.I save the file after adding the repository line.

---

### Post by akbarg64 on 2011-04-23
Someone is unable to answer my problem?

---

### Post by confused57 on 2011-04-23
I think you need to run upgrade?:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install remastersys

Does remastersys show up in Synaptic?

---

### Post by ~Plue on 2011-04-23
if you're sure the line is there in /etc/apt/sources.list it still doesn't show up in the package manager after you refresh the software index, you could install it using the deb file.
[http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.18-1_all.deb](http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.18-1_all.deb)

save the file and double click to install it (on 10.10 and newer, the software center and in older releases gdebi would open up and prompt you to install it)

---

### Post by wilee-nilee on 2011-04-23
I installed remastersys earlier this week I believe I had to run the update several time to capture the hit and have it show on my system, might have been another 3rd party hard to say. Check the /apt/sources.list and make sure it is there.

---

### Post by akbarg64 on 2011-04-24
Thanks to help friends. When the command sudo apt-get update I use
I get connection failures encountered. whether it is a problem for me or for you there. Please see the attached photos.

---

### Post by akbarg64 on 2011-04-24
> **confused57 said:**
> I think you need to run upgrade?:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install remastersys

Does remastersys show up in Synaptic?


no.

---

### Post by confused57 on 2011-04-24
> **~Plue said:**
> if you're sure the line is there in /etc/apt/sources.list it still doesn't show up in the package manager after you refresh the software index, you could install it using the deb file.
[http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.18-1_all.deb](http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.18-1_all.deb)

save the file and double click to install it (on 10.10 and newer, the software center and in older releases gdebi would open up and prompt you to install it)

Use the link ~Plue supplied, download & install from the .deb file.  That's how I did it when I used remastersys, which worked quite well for me; or just keep trying to update, as wilee-nilee suggested.

---

