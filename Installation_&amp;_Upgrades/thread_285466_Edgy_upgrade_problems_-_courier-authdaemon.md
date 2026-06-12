---
title: "Edgy upgrade problems - courier-authdaemon"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by DRHansen on 2006-10-26
Anyone else have problems with courier-authdaemon?
Install screwed up and left a broken index.  

Running "sudo apt-get install-f" doesn't fix it.  It finds that it needs "extra" packages courier-authdaemon & coureier-authlib and "new" package courier-authdaemon.

Proceeding after - Do you want to continue [Y/n]? Y
results in - Package is in a very bad inconstent state - you should reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error' what(): basic_string::_S_construct NULL or not valid
Aborted (core dumped)

Anybody got a clue what to do next? :confused: 

Thanks,

DRH

---

### Post by rmjb on 2006-10-26
Hi, you can try to Completely Remove the packages using Synaptic then re-installing.

If you've got this pacakge configured a certain way you'll loose your configurations however, so you should take note of that.

- rmjb

---

### Post by SecurityMonkey on 2006-10-27
I'm having the exact same issue.  I've tried to use Synaptic to force-remove the packages, but it still errors out.  

I've run dpkg --configure -a until I'm blue in the face.


  ](*,)

---

### Post by rmjb on 2006-10-27
Hi, unfortunatly this sees to be a bug, but it's being worked on. You can track the progress here:

[https://launchpad.net/distros/ubuntu/+source/courier-authlib/+bug/64615](https://launchpad.net/distros/ubuntu/+source/courier-authlib/+bug/64615)

- rmjb

---

### Post by formeroosid on 2006-10-27
Here's the solution that worked for me that is listed in the bug thread. 

```
1. backup /var/lib/dpkg/status to a safe location
2. remove all courier entries from /var/lib/dpkg/status (nano it, search=ctrl-w)
3. sudo apt-get upgrade
4. sudo apt-get install courier-imap

I now need to reconfigure courier, but at least it's working again!
```

Jamie

---

### Post by DRHansen on 2006-10-27
Ref: [launchpad thread on this problem]("https://launchpad.net/distros/ubuntu/+source/courier-authlib/+bug/64615")

1. rblake's fix didn't work for me.
> "sudo dpkg --force-remove-reinstreq -P courier-authdaemon"


2. HaroldAling's fix did work.
> 
   1. backup /var/lib/dpkg/status to a safe location
   2. remove all courier entries from     
      /var/lib/dpkg/status (nano it, search=ctrl-w)
   3. sudo apt-get upgrade
   4. sudo apt-get install courier-imap

HTH
DRH

---

### Post by SecurityMonkey on 2006-10-27
FIXED!

Thanks to HaroldAling.

1. backup /var/lib/dpkg/status to a safe location
2. remove all courier entries from /var/lib/dpkg/status (nano it, search=ctrl-w)
3. sudo apt-get upgrade
4. sudo apt-get install courier-imap

---

### Post by clee991 on 2006-10-27
same problem ... FIXED!...Thanks HaroldAling.

---

### Post by zek725 on 2006-10-29
what's courier anyway? Is it essential?

I had the same problem with the upgrade from Dapper. I've reinstalled Xubuntu 6.10 from scratch and it did not produce the same error. :D

---

### Post by thynk on 2006-10-31
thanks to formeroosid's posting here, I was able to MOSTLY finish the upgrade. There are a few problems and I had to reinstall all the courier components, no big deal!

However, my thunderbird is now telling me that "mail server xyz.domain.com is not an IMAP4 mail server" 

I've uninstalled and reinstalled courier-imap, checked the config in webadmin, and googled the error.  I'm stumped. 

Pop and webmail both work, but those are only fall back uses - I won't let this rest until I've got IMAP working again.

Any suggestions, any help anyone can provide would be grand!



Stu

---

### Post by harty83 on 2006-11-01
Same problem here.  Server not recognized as an imap server.  Help please!!??

---

