---
title: "re-install 10.04 or fix possible?"
date: 2012-03-19
forum: Installation &amp; Upgrades
---

### Post by 1centwiz on 2012-03-19
Installed 10.04 dual boot on a Gateway MX 6426, XP Media, AMD Turion 64m ATI Graphics.

Problems: unable to connect wireless, all known passwords will not work for direct connect for updates. (I have tried to find the password and change it, but that does not work either.) :confused:

There is an error when booting about something missing, but it runs so fast I can't read it all. Is there a way to freeze the screen so I can post the error? 

Or would it be easier to use a new download of 10. 04 on USB and override this installation with a new one?

Thanks!

---

### Post by TBABill on 2012-03-19
Is it asking for a WEP/WPA password or is it asking for a keyring password? They'll be different. Need to know specifically what you are being prompted to provide.

---

### Post by 1centwiz on 2012-03-19
I will log out and see, right now I'm on windows to try and get this taken care of...however, I need to wait until the new download is on the flash drive properly before closing and restarting. 

Thanks for the help, be back in a few!

---

### Post by 2F4U on 2012-03-19
> **1centwiz said:**
> 
There is an error when booting about something missing, but it runs so fast I can't read it all. Is there a way to freeze the screen so I can post the error?

Look into the log files, which are in /var/log. The system log file should have the error in it.

---

### Post by 1centwiz on 2012-03-19
I am updated to 2.6.38-11 
Ubuntu 11.4

I was able to upgrade using a cat 5 cable, and now the wireless works.

Currently using Ubuntu to answer this, however, when the screen shuts due to lack of activity, I am unable to log back in because I don't have my password.

How do I find my password and change it? :confused:

Thanks for you help!

---

### Post by 1centwiz on 2012-03-19
The error messages have been resolved by the upgrade. I don't know how it worked since I can not remember my password, but it worked.

Now I need to figure out how to find my password and change it and WRITE IT DOWN!

---

### Post by snowpine on 2012-03-19
To reset your password: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by 1centwiz on 2012-03-19
> **snowpine said:**
> To reset your password: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
This was extremely helpful... thank you. The problem is now fixed!

However, when I went to resume normal boot, it left me at the black screen to which I have not clue how to get out of. I tried the exit command and it stayed on the black screen and did not boot back to normal. Just a heads up about the tutorial as everything else worked like a charm. Thank you again!

---

### Post by snowpine on 2012-03-19
This should work if you find yourself in that situation again:

```
sudo reboot
```

---

### Post by 1centwiz on 2012-03-19
Thank you! Wrote it down next to my password~!

---

