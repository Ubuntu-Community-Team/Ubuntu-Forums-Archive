---
title: "Latest version of The Gimp"
date: 2012-12-16
forum: Installation &amp; Upgrades
---

### Post by theKuch on 2012-12-16
The latest version of The Gimp in the Software Centre seems to be 2.6 though on the gimp site says 2.8.2 has been released. Any reason the Centre is so far behind?

Thanks, Menachem

---

### Post by howefield on 2012-12-16
Look like 2.8 went into Ubuntu 12.10, presumably you are using an earlier version ?

Package versions are pretty much fixed at the time of release and save for security updates are not updated.

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

### Post by Cheesemill on 2012-12-16
Because that's the way Ubuntu works.

When a version of Ubuntu is released all the software available in the main repositories is frozen at whatever version was available at that time. Only bug fixes and security updates are pushed out.

For example if the latest version of Gimp available was 2.6.10 when 12.04 was released then it will only get upgrades to 2.6.11, 2.6.12 etc as these are bug fixes, 2.8 will never be available for 12.04 through the normal update channels.

The official method to get the latest version of software is to upgrade your system to 12.10.

If you want to install Gimp 2.8.x on Ubuntu 12.04 then you will have to use a PPA instead. PPA's are unofficial software repositories that have the latest versions of software, however, they are not officially supported by Canonical so support for any issues that may arise by using them will be harder to come by. You also have to trust that whoever runs the repository isn't going to add any malicious code (although this does get checked for).

To add the repository for Gimp to your system and then install the latest version simply run the following commands.

```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update && sudo apt-get install gimp
```

---

### Post by ajgreeny on 2012-12-16
I am using Gimp 2.8.x on my 12.04 installs of ubuntu and Xubuntu with no problems.

I am pretty certain the ppa shown above is totally safe and problem-free, so why not give it a try?

---

### Post by Cheesemill on 2012-12-16
> **ajgreeny said:**
> I am pretty certain the ppa shown above is totally safe and problem-free
Me too, I've used it on several machines.

I just wanted to make sure that theKuch had been informed of the risks of using a PPA.

---

### Post by theKuch on 2012-12-18
Thanks everyone.

I guess the question boils down to why am I still running 12.04?

I thought the upgrade manager always informs you of a new version? I haven't seen anything and I receive upgrades every few days.

---

### Post by mastablasta on 2012-12-18
> **theKuch said:**
> I thought the upgrade manager always informs you of a new version? I haven't seen anything and I receive upgrades every few days.
 
 
those ("every day" packages) are not upgrades but updates. 
you will receive upgrade info on next LTS (in 2014). but you can trigger them now if oyu want the non LTS version of the OS.
 
LTS (long term support) are supported for 5 years. they get bug fixes and security updates in this time. Making them a more stable version. the other releases are of more experimenta nature as new features are added and then tested and so on until the next stable release. you can read more about LTS special features here: [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by theKuch on 2012-12-18
Great. Thanks for the clarification.

---

