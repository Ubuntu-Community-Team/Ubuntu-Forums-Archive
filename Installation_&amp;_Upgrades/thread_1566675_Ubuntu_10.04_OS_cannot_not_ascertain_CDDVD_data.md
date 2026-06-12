---
title: "Ubuntu 10.04 OS cannot not ascertain CD/DVD data"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by RobertX on 2010-09-02
Well, I tried out the Ubuntu 10.04 CD/DVD and found something that was not to my liking. It seems that the operating system does not know how to recognise the Ubuntu CD/DVD's programs.

When I used the Synaptic Package manager to install OpenJDK, The manager tells me that there is nothing that it needs to install online, which was what I was expecting since that was what happens when I try to install OpenJDK in earlier versions of Ubuntu.Then it asks me to insert the CD. I did that as well. I inserted the CD and it asks again. So I OK'ed. Then it says "some files cannot be retrieved", as shown in the picture.

I could just download this online, but I don't want to because I don't want to go the time to download the same software again from the Internet; I don't have the time.

Please tell me if you want to - oh, I have two drives. Should that information help?

Thanks.

---

### Post by jerenept on 2010-09-02
if you want openJDK java and other media/browser plugins, you could install the package "ubuntu-restricted-extras"
```
sudo aptitude install ubuntu-restricted-extras
```
you will need a working internet connection.

forgive me if i do not understand your problem though, your grammar isn't the best.

---

### Post by RobertX on 2010-09-02
Fine, rocket scientist. I'll further clarify.

For instance, I want OpenJDK, the past versions supplied it offline, and this one didn't.

Me want offline software. Got it?

---

