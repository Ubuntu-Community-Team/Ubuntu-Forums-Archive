---
title: "won't connect to internet most of the time"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by bigcanuck on 2005-11-19
this is a weird problem to me I've connected twice to the interenet but normally it will not.  As far as I can tell everything is set up right.  I have Compaq's R4000 Amd64 bit.  Any ideas anyone, or does anyone have any sugguestions as to change which settings to make it work all the time.

---

### Post by pompeyjohn on 2005-11-20
more information please.... go into networking, and tell us what you have written in there. dont worry, there are loads of people on here keen to help. It is easier to help people that have supplied loads of information, so whenever you have a problem, try and supply as much as possible. If you are not sure what is needed, add it anyway. I am sure most people would rather just skip a few lines, than ask for more information. In this case, what would be really helpful is as much info as possible about how you connect to the internet normally. A good place for this info would be under system/administration/networking.

cheers

---

### Post by bigcanuck on 2005-11-20
ok, my default gateway is eth0 which is my ethernet card, it is set as active, is enabled and is set up with DHCP.   My hostname is set as ubuntu.  my Dns servers are set correctly to the domain uvic.ca.  Like I said it's rather hit and miss.  I have a compaq R4000 64bit laptop.  It will work perfectly fine at times but most of the time it will not connect.  My intenet connection is fine as It works in windows and on my roomates computer.  I never do anything speacial to get the interenet working, I just boot up and then try and go on, if it doesn't work then I reboot, and eventually it will connect.

---

### Post by pompeyjohn on 2005-11-20
ok, so you are connecting to the internet through a remote computer right? From a console can you do the following;

cat /etc/resolv.conf

and make a note of what that says - both when you have an internet connection, and when you dont.

Cheers,

---

### Post by bigcanuck on 2005-11-20
it's not through a remote computer... sorry that was unclear, it's a university subnet, so I'm withing the university network.  But here's the info for online; 
search uvic.ca
nameserver 142.104.0.18
nameserver 142.104.0.17

---

### Post by pompeyjohn on 2005-11-22
and when there is no internet connection........

---

### Post by bigcanuck on 2005-11-23
sorry had exams lately and haven't had time to play with ubuntu,

there is no information, I just get blanks in all the fields

---

### Post by pompeyjohn on 2005-11-23
no worries - hope the exams are going well

by blank in all the fields you mean in the networking applet? sorry, I should have been more clearer - next time your internet goes down run the following from the terminal

cat /etc/resolv.conf

and make a note of what that says.

This is just a guess but I think what might be happening is that you are having a  problem with DNS name servers. The resolv.conf file lists the ones your system uses. I am guessing that when all is ok you see ..

search uvic.ca
nameserver 142.104.0.18
nameserver 142.104.0.17

and that when you have no internet connection you'll see nothing in /etc/resolv.conf or something different to the above. 

This is just a hunch mind you, but this is a process of trial and elimination, and I think this would be a good way of working out if the outage is DNS related.

Dont feel the need to rush back - drop a line whenever you can. Your exams are important!! :D

---

### Post by bigcanuck on 2005-11-24
here are the offline stats:

uvic.ca
nameserver:192.168.2.1

so yes I do believe it's DNS related however I'm not sure how to go about fixing that, I watched it carefully during start up the last time and I got "Temporary name failure" just after trying to synchronize the clock with ntp.ubuntu.org

---

### Post by pompeyjohn on 2005-11-28
sorry about not getting back to you sooner - am just recovering now from a heavy thanksgiving weekend.

yep, looks like DNS to me. What I am going to suggest is that we set the DNS information in resolv.conf manually, and then try to disable the bit of code which updates that file. It should not cause any problems for you elsewhere. I have done it on mine, and to no ill effect. It works on the machine I am typing this on..... but, I dont know if this is the most elegant solution.

ok,.... once you have the nameservers set in resolv.conf you need to edit the following file as root:

/etc/dhcp3/dhclient-script

now what you are looking for is a section which starts with:

```
make_resolv_conf() {
```

and ends with 

```
mv $new_resolv_conf /etc/resolv.conf
fi
}
```

This is the code I think is rewriting your resolv.conf file and as a result dropping you from the internet. What you need to do is comment out this code to stop it running. To do this proceed every line in this section with # So the first line would look like this:

```
#make_resolv_conf() {
```

Save the file. Now - check your resolv.conf to make sure nothing changed whilst you were doing that editing. If it did, type in the correct nameservers again.

Reboot, and keep an eye out for that NTP - it should sync fine as the DNS will resolve correctly - and you should have no more problems with dropped connections. I hope.

Get back to me on this if you can because is this doesnt work, well, we'll try something else!! :D

---

### Post by bigcanuck on 2005-12-02
I actually, through playing around did something similar to that and got it working between the posts but thank you very very much for your help

---

