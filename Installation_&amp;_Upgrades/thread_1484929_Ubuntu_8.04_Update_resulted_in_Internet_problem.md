---
title: "Ubuntu 8.04 Update resulted in Internet problem"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by joeysat on 2010-05-16
Hi,

I was using Ubuntu 8.04 in a dual boot system with Windows XP. Everything seemed fine until I decided to upgrade to Ubuntu 10.

As instructed I decided to apply all updates to the existing version before upgrading. While doing so, everything worked fine but after installing the updates and restarting the system, the internet does not work at all in the updated version of Ubuntu 8.04.

I am using an ADSL connection and earlier the internet used to work fine.. I had installed all settings as per the official documentation. Now since its not working I tried to reconfigure it by using 'sudo pppoeconf' and I get the message

"Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pope process which controls the model" 

please suggest appropriate steps... thanks!

---

### Post by dE_logics on 2010-05-16
It might happen that if your ppp daemon does not get adequate permission it just keeps on running, so you gotta kill that.

Anyway, first see if this works - 

[http://ubuntuforums.org/showthread.php?t=1481146](http://ubuntuforums.org/showthread.php?t=1481146)

Short one :)

---

### Post by joeysat on 2010-05-17
Thanks for the response.. but it didnt help :(
First of all, I am not in a multi user environment.. still I gave the permission like you asked me to. After doing that I was not able to change the DSL settings like you asked me to..

One other thing.. earlier when the internet used to work, I remember seeing two connections eth0 and eth1.. now there is only one... does this mean anything? 
I also have to mention that I am still using Ubuntu 8.04 since after the initial updates internet is not working and I am not able to update/upgrade further..

Looking forward to your help... I used to love Ubuntu so much but now... :(

---

### Post by kansasnoob on 2010-05-17
I've had very few internet problems with Ubuntu, therefore I'm a dummy on the subject, but see if the Broadband section of this is at all helpful:

[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)

---

### Post by joeysat on 2010-05-17
Thanks for the link kansasnoob... but it is only a how-to section which I have already used. Like I said earlier I had configured internet using ADSL pppoe years back, it is only now when I tried to apply some updates that it is not working :(

I am guessing that Ubuntu is not able to detect my ethernet card... could you guys help me with that?

dE_logics, how do I kill existing pppoe processes?

---

### Post by PDA1 on 2010-05-18
This might help.....



Problem- no Networking enabled with Ubuntu 10.04. 
 Network connection was lost 1 day after I upgraded from 9.10. I couldn't connect to the web with wireless or ethernet and Networking was grayed and said it was “disabled” 
 The steps are numbered below 
 (DO NOT enter the numbers when you're using Terminal)(anything in quotes marks doesn't need to be typed- they are there for reference only)
 
Here's how I fixed it- 
 Start TERMINAL 
 
[LIST=1]
[*]     sudo Nautilus
[/LIST]
 
[LIST=1]
[*]     Go to the folder /var/lib/NetworkManager/ 
[*]     Edit the file NetworkManager.state to read “setting NetworkingEnabled=true” 
[*]     Save the edited NetworkManager.state file 
[*]     Close Nautilus 
[*]     Using TERMINAL type “sudo restart network-manager”
[/LIST]
  This should enable networking again. I hope it works for you.....believe it or not it did for me.

---

### Post by joeysat on 2010-05-18
actually I have not yet upgraded to Ubuntu 10.04, I am still in 8.04.. so can I use this for that as well?

---

### Post by joeysat on 2010-05-19
I tried to do as you said PDA1.. but I got the following message and could not proceed further.. can you please let me know what can be done to correct this?

> ** (nautilus:6067): WARNING **: Unable to add monitor: Operation Not supported

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by PDA1 on 2010-05-19
What I have to do to get Nautilus to do what I want for the edit is...

sudo Nautilus


Hope that helps.

---

### Post by joeysat on 2010-05-19
I got the error message mentioned in my previous post only when I typed 'sudo nautilus' in Ubuntu 8.04... how do I  correct that error?

Thanks!

---

### Post by PDA1 on 2010-05-19
The only help I can provide you with is the instructions I provided above.  For my fix to work you have to do as I wrote.  You're not even in the correct folder to find and edit network- this is the folder ------> /var/lib/NetworkManager/

Assuming that your network manager is located there.

---

### Post by dE_logics on 2010-05-21
> After doing that I was not able to change the DSL settings like you asked me to..

Hummm...post the output of > groups <your username>

---

### Post by PDA1 on 2010-05-21
You haven't upgraded to 10.04? You said you did in the first post.

My fix only worked for my system running 10.04.

Sorry, can't help.

---

