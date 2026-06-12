---
title: "Unable to extract into the /opt folder"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by aboutell on 2010-12-07
Greetings All,

I am still sort of a newbie when it comes to Ubuntu and Linux for that matter, but I am attempting to setup a webserver on an Ubuntu machine using XAMPP and Drupal (Web Content Manager).  I have already downloaded both files, but when I attempt to run the sudo command to install them I get an error that says that I don't have the appropriate permissions to complete this.  I have checked and I am an administrator on my machine.

Can anyone please assist?

Thanks

---

### Post by grizzler on 2010-12-07
What's the exact command you are trying to run? Keep in mind that what's mentioned on the XAMPP-site is not quite correct for Ubuntu.

When I installed XAMPP, I used something like:
```
sudo tar -xzf xampp-linux-1.7.3a.tar.gz -C /opt
```

---

### Post by aboutell on 2010-12-07
Grizzler,

I attempted the code that you did and here is the below is the error I get:

adminst@SC-UBUNTU1:~$ sudo tar -xzf xampp-linux-1.7.3a.tar.gz -C /opt
tar (child): xampp-linux-1.7.3a.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now


The files are downloaded into my download folder within Places.

Let me know!
Thanks

---

### Post by coffeecat on 2010-12-07
You are getting an error because you are running that command in your home directory:

> **aboutell said:**
> adminst@SC-UBUNTU1:~$ sudo tar -xzf xampp-linux-1.7.3a.tar.gz -C /opt

The '~$' prompt tells you that you are in home. But your tar.gz file is in your Downloads directory. Note the capital-D. Linux is case-sensitive. If you're used to using a Windows command prompt, you need to beware of this. Anyway, cd to Downloads:

```
cd Downloads
```... and you'll get a '~/Downloads$' prompt telling you where you are. Now your sudo tar command should work.

By the way, take advantage of auto-completion in the terminal. Type 'cd Do' and then press the TAB key and 'Downloads' will be autocompleted for you.

---

### Post by aboutell on 2010-12-07
Coffeecat,

Thanks for your help!  This worked!!

Andrew

---

### Post by ravinderkaur on 2012-04-19
Hey...Thanksss Coffecat...it worked for me as well !:)

---

