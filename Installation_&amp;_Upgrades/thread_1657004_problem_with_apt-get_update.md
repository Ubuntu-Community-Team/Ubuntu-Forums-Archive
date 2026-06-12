---
title: "problem with apt-get update"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by samsanchez on 2010-12-31
I get these errors when I do **sudo apt-get update**.(There are other outputs before this, but I won't post the entire output unless someone thinks is is relevant.

```
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://gb.archive.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```Does anyone know the cause of these errors and how I can resolve them?

---

### Post by drs305 on 2010-12-31
Try adding the correct repository key with this command:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3E5C1192 437D05B5
```

---

### Post by samsanchez on 2011-01-01
Thanks for the suggestion.

That didn't seem to work, though. I get the following output:

```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 3E5C1192 437D05B5
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" 20 new signatures
gpg: no ultimately trusted keys found
gpg: Total number processed: 2
gpg:              unchanged: 1
gpg:         new signatures: 20

```

But **sudo apt-get update** still returns the following errors:

```
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://gb.archive.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by drs305 on 2011-01-01
Open up Synaptic or Software Sources, Settings, Repositories, go to the Authentication tab, and highlight the appropriate entries and delete them. They will be added the next time you run the update. Since it didn't like the ones provided via command line, try changing servers in Synaptic/Software Sources. If that still doesn't solve it, try running the previous command once again on a new server.

---

### Post by Nuukee on 2011-01-05
Hi,
same for me. I am not aware that I changed anything, but since a few days there is a red triangle in my notification area complaining about:

```
W: An error occurred during the signature verification. The repository  is not updated and the previous index files will be used. GPG error:  http://extras.ubuntu.com maverick Release: The following signatures were  invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic  Signing Key <ftpmaster@ubuntu.com>

W: An error occurred during the signature verification. The repository  is not updated and the previous index files will be used. GPG error:  http://security.ubuntu.com maverick-security Release: The following  signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive  Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  


```


I tried both suggestions here (add the keys via cmdline, delete server in GUI), but the problem remains.
Any other ideas?

Thanks in adanvce,
Sven
(new to this forum but a satisfied Ubuntu user for years)

---

### Post by drs305 on 2011-01-05
> **Nuukee said:**
> I tried both suggestions here (add the keys via cmdline, delete server in GUI), but the problem remains.
Any other ideas?

Try this (it repeats some of what you have done but perhaps more completely):
Change the server to US [http://www.gtlib.gatech.edu/pub/ubuntu](http://www.gtlib.gatech.edu/pub/ubuntu) (It's one of the last listings under US and I know it is working). (Synaptic, Settings, Repositories, Ubuntu Software tab > Download from: )

In the Authentication tab, remove the "Ubuntu Archive Automatic Signing" entry.

Import the key:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5
```

Update:
```
sudo apt-get update
```

---

### Post by Nuukee on 2011-01-05
Thanks for the fast reply!
Worked like charm for the second error message I got (Ubuntu Archive  Automatic Signing Key), the first one is still there :-(  (Ubuntu Extras Archive Automatic Signing Key).

I did import the key though, as you explained:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3E5C1192
and
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5

and changed the server to the one you mentioned.

---

### Post by drs305 on 2011-01-05
> **Nuukee said:**
> the first one is still there :-(  (Ubuntu Extras Archive Automatic Signing Key).

I did import the key though, as you explained:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3E5C1192


I didn't have Ubuntu Extras installed but did so and the key appeared in the Authentication tab listed as "Ubuntu Extra Archives ..." Did you try removing that key as well, and then rerun the import command for key 3E5C1192 ?

---

### Post by Nuukee on 2011-01-05
Yes, that's exactly what I did.

---

### Post by presence1960 on 2011-01-05
I had the same problem. After many attempts to fix it I generated a new sources.list from [here]("http://repogen.simplylinux.ch/index.php")

Made a backup copy of my original sources.list then replaced all text in the original sources.list file with the generated output from the website. Then ran the listed commands to import proper key files. Worked like a charm!

---

### Post by Nuukee on 2011-01-10
Thanks everybody!
I tried the the procedure from the last post.
It works, but I do not have the extras repository any more, which caused the error message, so the problem is gone obviously ;-)
Anyway, no big deal, I am sticking with that for now, my errors are gone.

Thanks to everybody who helped! I really appreciate this :-)

---

### Post by sadimr9 on 2011-01-10
Hello friends.

I'm new on this forum, also new on ubuntu.

when I'm using update I'm getting this error.

--------------------------------------------------------------

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FE8956A73C5EE1C9


--------------------------------------------------------------

can anyone help me to solve this issue as soon as possible.

I really need help. please.

Thanks,
Sadi.

---

### Post by oldos2er on 2011-01-10
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
```

where KEYID is number shown in error msg.

---

### Post by neaj on 2011-01-14
> **oldos2er said:**
> ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
```

where KEYID is number shown in error msg.

jean@klippie:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

jean@klippie:~$ sudo apt-get update
[...]
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by drs305 on 2011-01-14
> **neaj said:**
> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Try clearing the existing Ubuntu Extras key via Synaptic or Software Sources. Synaptic: Settings, Repositories, Authentication tab. Find the Ubuntu Extras entry (and make sure there isn't a duplicate), highlight it and select 'Remove'. This should remove the Ubuntu Extra keys, including any bad keys that may be stored by Ubuntu.

You could also try from the terminal:
```
sudo apt-key del 16126D3A3E5C1192
```

Then run *oldos2er's* command again to add the valid key back.

---

### Post by gregandkelly1 on 2011-01-28
Hi - I have a similar problem.

I have the following GPG Errors
```
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG F13930B14BB9F05F Launchpad PPA for jcfp
GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```So I ran the following commands
```
sudo apt-key del 40976EAF437D05B5
sudo apt-key del F13930B14BB9F05F

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F13930B14BB9F05F
```But I still get the same GPG errors?   

Any ideas?   Ive tried generating my own sources.list from [http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php) and also using the default one.  Also tried changing to main server and local nz server as well but still no luck.



Edit:

Changed servers again to a local NZ one and only one GPG Error
```
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG F13930B14BB9F05F Launchpad PPA for jcfp
```

---

### Post by drs305 on 2011-01-29
> **gregandkelly1 said:**
> 
Changed servers again to a local NZ one and only one GPG Error

gregandkelly1,

Welcome to the Ubuntu forums. Instead of trying to add the BADSIG key, just delete it with the first command, then run the update. See if it gives you a new 'missing' key error message - it may be a different alphanumeric sequence. If so, then use the apt-key command to add the new key.

---

### Post by asamf on 2011-06-20
> **gregandkelly1 said:**
> Hi - I have a similar problem.

I have the following GPG Errors
```
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG F13930B14BB9F05F Launchpad PPA for jcfp
GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```So I ran the following commands
```
sudo apt-key del 40976EAF437D05B5
sudo apt-key del F13930B14BB9F05F

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F13930B14BB9F05F
```But I still get the same GPG errors?   

Any ideas?   Ive tried generating my own sources.list from [http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php) and also using the default one.  Also tried changing to main server and local nz server as well but still no luck.



Edit:

Changed servers again to a local NZ one and only one GPG Error
```
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG F13930B14BB9F05F Launchpad PPA for jcfp
```

for gpg errors run this simple code in terminal
>                                                         sudo bash
 apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

        

:lolflag::lolflag::lolflag:

---

### Post by omunozsj on 2012-02-03
February 3rd, 2012. Oneiric. asamf's solution still works for same error. It seems that lists get corrupted.


I must say that I didn't create the folder lists/partial, I'd just update and it works.

---

### Post by raja.genupula on 2012-02-03
hi after seeing many problems with this issue i have googled for any package directly which can handle and got this .

[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

I hope that will help you for future usage. 

cheers 

Raja

---

### Post by Flanmaster on 2012-02-03
I would like to offer that I had this problem after installing Lubuntu 11.10 on an old presario v3000.  I found that connecting it to a wired connection and rebooting did the trick for me.  I don't know why but it did.

---

### Post by Sealbhach on 2012-08-26
```
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

Those commands fixed my problems. 

.

---

