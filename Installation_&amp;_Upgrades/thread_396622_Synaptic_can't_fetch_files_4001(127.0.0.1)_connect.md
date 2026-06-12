---
title: "Synaptic can't fetch files: 4001(127.0.0.1) connection refused"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by paulwheeler on 2007-03-29
Running Dapper 6.06 LTS for a few months. Now every time I try to add programs using synaptic, I  get  the following error message(s): 

W:Failed to fetch [http://archive.ubuntu.com/ubuntu/poo/main/e/evolution-data-server/libedataserver1.2-7_1.6.1-0ubunutu7_i386.deb](http://archive.ubuntu.com/ubuntu/poo/main/e/evolution-data-server/libedataserver1.2-7_1.6.1-0ubunutu7_i386.deb)
 Could not connect to localhost:4001(127.0.0.1). - connect (111 Connection refused)

This is same for any and all files to be updated.

Obviously, I get the same message when I click on the white and orange updates available icon near the date.

What is happening?  [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif) Any ideas on what to do are appreciated.

---

### Post by dcstar on 2007-03-29
> **paulwheeler said:**
> Running Dapper 6.06 LTS for a few months. Now every time I try to add programs using synaptic, I  get  the following error message(s): 

W:Failed to fetch [http://archive.ubuntu.com/ubuntu/poo/main/e/evolution-data-server/libedataserver1.2-7_1.6.1-0ubunutu7_i386.deb](http://archive.ubuntu.com/ubuntu/poo/main/e/evolution-data-server/libedataserver1.2-7_1.6.1-0ubunutu7_i386.deb)
 Could not connect to **localhost:4001**(127.0.0.1). - connect (111 Connection refused)
........

It seems you have set Synaptic to use a Proxy server, go into it and change the preferences back to whatever network setup you are using.

---

### Post by paulwheeler on 2007-03-29
Thanks for the hint, but it was still set for direct connect to the internet just like it always has been. :( 

Any other ideas?

paul

---

### Post by dcstar on 2007-03-30
> **paulwheeler said:**
> Thanks for the hint, but it was still set for direct connect to the internet just like it always has been. :( 

Any other ideas?

paul

Not really, if could be some config file has got corrupted, can you put those URLs in your browser and download the files manually to your PC?

---

### Post by Augustin on 2007-03-30
> **paulwheeler said:**
> Running Dapper 6.06 LTS for a few months. Now every time I try to add programs using synaptic, I  get  the following error message(s): 

W:Failed to fetch [http://archive.ubuntu.com/ubuntu/poo/main/e/evolution-data-server/libedataserver1.2-7_1.6.1-0ubunutu7_i386.deb](http://archive.ubuntu.com/ubuntu/poo/main/e/evolution-data-server/libedataserver1.2-7_1.6.1-0ubunutu7_i386.deb)
 Could not connect to localhost:4001(127.0.0.1). - connect (111 Connection refused)

This is same for any and all files to be updated.

Obviously, I get the same message when I click on the white and orange updates available icon near the date.

What is happening?  [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif) Any ideas on what to do are appreciated.


My guess is that either you or someone else has changed the network settings. The 127.0.0.1 is the address of localhost, not an Internet address.

---

### Post by paulwheeler on 2007-03-30
Per David's suggestion, I pasted the address into web browser. Now I get a File Not Found error.
Clicking on the link in this post also gets a File Not Found error.

In answer to Augustin's comment, I am the only user/administrator on this computer, and I am also the only network administrator. The network settings have not changed.

No I am not running a proxy, and yes, I know about 127 addresses.

---

