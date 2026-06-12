---
title: "parse error"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by ISIRC10 on 2011-06-08
I was running an update on my computer (running Ubuntu 10.04 Lucid) and something must have been transferred incorrectly as every time I open synaptic, I get an error message that tells me to type a command into the terminal:
```
sudo dpkg --configure -a

```

After doing that, it displays this:
```
dpkg: parse error, in file '/var/lib/dpkg/updates/0001' near line 0:
 newline in field name `#padding'

```
What can I do to solve this? I am just getting into terminal commands and this whole error thing seems a bit over my head at the moment...:(

---

### Post by mörgæs on 2011-06-08
Try to restart the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```Please post the error messages, if any.

---

### Post by ISIRC10 on 2011-06-08
So I ran sudo apt-get clean and nothing came up
Then I ran sudo apt-get update and a list of packages/sources came up, followed by this message: 
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

Then I ran sudo apt-get upgrade and then same message appeared.
I ran the command in the message (sudo dpkg --configure -a) and this appeared:
```
dpkg: parse error, in file '/var/lib/dpkg/updates/0001' near line 0:
 newline in field name `#padding'
```
What should I do now? (Oh, and thank you so much for helping me out!)

---

### Post by mörgæs on 2011-06-08
Then we must delete the file making the trouble:

```
sudo rm /var/lib/dpkg/updates/0001
```After that, please run the commands again.

---

### Post by ISIRC10 on 2011-06-08
I deleted the file and ran the commands again.
After sudo apt-get update, I go this message:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```
So I ran the command and now it is a different error:
```
dpkg: parse error, in file '/var/lib/dpkg/updates/0007' near line 0:
 field name `lla/Entrust.net_Secure_Personal_CA.crt,' must be followed by colon

```
Do I need to do something with the file now?

---

### Post by ISIRC10 on 2011-06-08
looking at that file, it doesn't seem to be complete (its actually a different format than the others) This is what it contained - it looks like it got cut off (part of the initial "mozilla" was added to the last line?). What should I do with it?

The file:```

lla/Entrust.net_Secure_Personal_CA.crt, mozilla/Entrust.net_Secure_Server_CA.crt, mozilla/Entrust_Root_Certification_Authority.crt, mozilla/Equifax_Secure_CA.crt, mozilla/Equifax_Secure_eBusiness_CA_1.crt, mozilla/Equifax_Secure_eBusiness_CA_2.crt, mozilla/Equifax_Secure_Global_eBusiness_CA.crt, mozilla/Firmaprofesional_Root_CA.crt, mozilla/GeoTrust_Global_CA_2.crt, mozilla/GeoTrust_Global_CA.crt, mozilla/GeoTrust_Primary_Certification_Authority.crt, mozilla/GeoTrust_Universal_CA_2.crt, mozilla/GeoTrust_Universal_CA.crt, mozilla/GlobalSign_Root_CA.crt, mozilla/GlobalSign_Root_CA_-_R2.crt, mozilla/Go_Daddy_Class_2_CA.crt, mozilla/GTE_CyberTrust_Global_Root.crt, mozilla/GTE_CyberTrust_Root_CA.crt, mozilla/IPS_Chained_CAs_root.crt, mozilla/IPS_CLASE1_root.crt, mozilla/IPS_CLASE3_root.crt, mozilla/IPS_CLASEA1_root.crt, mozilla/IPS_CLASEA3_root.crt, mozi 
```

---

### Post by mörgæs on 2011-06-09
Just delete it. It will be rebuilt next time.

```
sudo rm /var/lib/dpkg/updates/000*
```

---

### Post by ISIRC10 on 2011-06-09
Right - so I deleted about five update files (all of them had similar errors) and then I got a breakthrough. Update ran and showed that there was still an error, this time accessing the yiff-server (it's a sound driver?)

Anyway, I was able to get back into synaptic and uninstalled the server - problem solved! The update and Upgrade commands both work, and my computer is happy again! (I just need to reboot and see if everything still works)

Thanks for the help, I will mark this as solved.

---

