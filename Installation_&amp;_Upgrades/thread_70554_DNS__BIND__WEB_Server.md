---
title: "DNS / BIND / WEB Server"
date: 2005-09-30
forum: Installation &amp; Upgrades
---

### Post by CYHPT.net on 2005-09-30
Hi all,

I've been tryin to search for a thread with DNS/BIND installation setup guide but I cant seem to find any. Plus Im new to this and I really need to know how you can actually do it in Ubuntu.

Im tryin to get my web server up on the internet for everyone (publicly), and have got a domain name with godaddy.com (the best DNS registrar), and tryin to set it up at home (meaning A host and etc...). I can do this easy on WIndows, but because I dont have a legit copy of it, I need to use an open-source OS like Ubuntu so that I can run a business without any problems.

Im really lost with Ubuntu, and I really wan to know all about Ubuntu as it is currently the best and hopefully it will be in the future so that I wont have to change my OS again. ANyways....

Can someone please tell me how I could set everything up? Maybe a guide perhaps? A link? I really need to get my Ubuntu running ASAP.

Thanks for reading and hope to get some guidance from all you Ubuntu experts.

Thanks in advance.. :)

CYHPT.net

---

### Post by adwait on 2005-09-30
I don't remember whether ubuntu comes installed with apache2(web server software) or not, so I am just gonna tell you the steps starting with installation......skip as required. Open up a terminal window, to do that.......right click and open terminal window. Use your user password when it asks for a password.
```

sudo apt-get install apache2
sudo /etc/init.d/apache2 start

```

The first command will download and install the software, if its already there, it will tell you so. The second will start it up.

Now, move the files you want to be available on your website to /var/www/.
```

sudo nautilus /var/www

```
This will open up a window of that directory. Not just drag and drop any files you want. Otherwise you can transfer the files using mv (I thought you are new to linux, so you might not know how do that.......)

You are done......enter your ip address in a web browser and you should see your wesbite.

---

### Post by CYHPT.net on 2005-09-30
Thanks for the tips, Im not really new to linux, just new to Ubuntu linux thats all. :)

Anyways, Im tryin to get my domain name going, how do I go about doing this?

Thanks,
CYHPT.net

---

### Post by adwait on 2005-09-30
For that you will have to set your domain name to point to the ip address of your computer.....I guess you'll just have to login to the control panel of godaddy.com, and then point the domain to your ip address.

---

### Post by CYHPT.net on 2005-10-03
Sorry, Dont you have to configure the A records in Ubuntu to have your web server running with domain names??

---

### Post by CYHPT.net on 2005-10-05
Hi guys,

I got my domain name and trying to set the records up so that ppl can access my website publicly, how do I configure this so it points to my domain name?

Can someone pls help me thanks..

---

