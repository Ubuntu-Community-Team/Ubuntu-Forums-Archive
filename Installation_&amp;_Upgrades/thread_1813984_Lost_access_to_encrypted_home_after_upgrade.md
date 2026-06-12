---
title: "Lost access to encrypted home after upgrade"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by lime3k on 2011-07-28
Hi,

I just tried reinstalling ubuntu 11.04 from the live disc, installation went well but afterwards I cannot get access to my home directory which is encrypted and I stupidly forgot to note the mount passphrase. is there anything I can do? where would the mount passphrase be stored from the previous installation and is there any chance of recoving it. Home and the root are on the same drive and the installation did not format the drive.

Please help, I'm really desperate here.

Thanks

---

### Post by blackbird3216 on 2011-07-28
This happened to me when I was upgrading from 8.10 to 9.10. Grub crashed, and I ended up having to do a fresh install, but my files, just like yours, were encrypted. I was really sad. 

After hours of searching, though, it turned out that I couldn't access my files because of a privedge problem. My new user (in the new installation) couldn't access the old files, since only the old user had access to it. 

But there is a loophole that I discovered. What I ended up having to do is to boot up the live cd, and then use a command to copy my files from the directory to my flashdrive. Oddly enough, although I didn't have access, the superuser (sudo) on the live cd did have access, so I was able to get my files out. 

I don't quite remember how I did it though, but I think it is possible for you to do the same. If more experienced members don't guide you, then I will try to find the commands when I get home. 

Good luck!

---

### Post by lime3k on 2011-07-29
I wonder if you're right and it is a privedge problem as I had changed my password but used the same username when prompted during the upgrade.

Could someone shed some light on this situation as I still don't understand how this all works. I'll be attacking the wiki tonight on the subject.

---

### Post by lime3k on 2011-07-29
Tried changing my password to the old, still no luck and I can still see the home directory is there occupies the same space it did before.

Any more insights? I'm fully prepaired to loose it all but I'd first like to know if there's any chance I could save it before I commit.

Thanks

---

### Post by lime3k on 2011-07-30
I've managed to recover what I think is my mount passphrase after finding the "recovering mount passphrase" section here:

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Mount%20Passphrase](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Mount%20Passphrase)

who knew! I've managed to  login from the installed OS which wasn't letting me into my home directory due to permissions.

Ive now added the passphrase to the key ring and tried mounting the encrypted Private directory with the following command, as per instructions found at previous link:

```
sudo mount -t ecryptfs /home/will/.Private /home/will/Private
```

which is returning an error:

```
Error attempting to evaluate mount options: [-95] Operation not supported
Check your system logs for details on why this happened.

```

Looking at the system log gives some more detail:

```
Jul 30 09:54:36 Willslap mount.ecryptfs: ecryptfs_get_module_ciphers: opendir error on [/lib/modules/2.6.38-10-generic/kernel/crypto]. Cannot get a list of ciphers available as modules.
Jul 30 09:54:36 Willslap mount.ecryptfs: init_ecryptfs_cipher_param_node: Unable to detect any available kernel ciphers; bailing out
Jul 30 09:54:36 Willslap mount.ecryptfs: fill_in_decision_graph_based_on_version_support: Error initializing cipher list; rc = [-95]
Jul 30 09:54:36 Willslap mount.ecryptfs: ecryptfs_process_decision_graph: Error attempting to fill in decision graph; rc = [-95]
```

I'm stuck from here, any suggestions as to solving this problem with mount?

---

### Post by lime3k on 2011-08-01
bump

---

### Post by lime3k on 2011-08-04
bump

---

### Post by Megaptera on 2011-08-04
Is this guide any help?

[http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)

---

### Post by lime3k on 2011-08-05
Thanks [Megaptera]("http://ubuntuforums.org/member.php?u=534545"), I'll go through the steps again outlined in the link. Thanks again

---

### Post by Megaptera on 2011-08-05
You're welcome! Let's hope it works!

---

### Post by lime3k on 2011-08-07
> **Megaptera said:**
> You're welcome! Let's hope it works!

No word of a lie, Megaptera, I love you! Worked a charm, thanks so much.

Anyone who finds themselves in this situation just follow the above guide.

```
**sudo ecryptfs-recover-private**
```

Thank you to everyone

---

### Post by Megaptera on 2011-08-08
You're very welcome!!

---

