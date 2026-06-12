---
title: "Could not download the upgrades (Size mismatch)"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by i_ReEm on 2011-06-19
Hi,
I have Ubuntu 10.10 installed and a few weeks ago I tried upgrading to 11.04 using "Update Manager" BUT I got the following error after a few hours of fetching all the files from internet except for one 

```

Could not download the upgrades

The upgrade has aborted. Please check your Internet connection or installation media and try again. All files downloaded so far are kept.

Failed to fetch http://sy.archive.ubuntu.com/ubuntu/pool/main/libp/libproxy/libproxy0_0.3.1-2ubuntu5_amd64.deb Size mismatch
Failed to fetch http://sy.archive.ubuntu.com/ubuntu/pool/main/libp/libproxy/python-libproxy_0.3.1-2ubuntu5_all.deb Size mismatch
```

I thought there's something wrong with the internet connection in spite of that everything else works well.. I tried upgrading in different times in different days, I redid the process again today and I got the same error again.
Any help?
Is there any other way to upgrade or ignore this package?
Thanks in advance

---

### Post by Rubi1200 on 2011-06-19
Hi,

start by trying these commands in the terminal:

```
sudo apt-get clean

sudo apt-get update
```

Let us know if this helps.

---

### Post by i_ReEm on 2011-06-20
> **Rubi1200 said:**
> Hi,

start by trying these commands in the terminal:

```
sudo apt-get clean

sudo apt-get update
```

Let us know if this helps.

No :( it didn't help.. I get the same error again :(

---

### Post by Rubi1200 on 2011-06-20
Just so you know, pinning this down and finding the solution might take a few steps so please be patient.

Try this next;

[B]System->Administration->Synaptic Package Manager ->Settings->Repositories->Download from 
[/B]
change the server to Main Server and then Reload and try again.

---

### Post by i_ReEm on 2011-06-20
OK..
Thank you for your help.
I tried that and I got the same error again:
```

Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libp/libproxy/libproxy0_0.3.1-2ubuntu5_amd64.deb Size mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libp/libproxy/python-libproxy_0.3.1-2ubuntu5_all.deb Size mismatch

```
I will be patient .. no problem :)

---

### Post by Rubi1200 on 2011-06-21
okay, I have another possible solution here:
[http://ubuntuforums.org/showthread.php?t=988241](http://ubuntuforums.org/showthread.php?t=988241)

---

### Post by i_ReEm on 2011-06-21
I think my country is blocking all the url with "proxy" in it, that's why I can't download these packages..
Someone downloaded these two packages for me.. now what should I do?

---

### Post by Rubi1200 on 2011-06-21
If I am not mistaken, you can just click on the package and it should open and allow you to install it. 
I think the default is to open it in Ubuntu Software Center.

---

