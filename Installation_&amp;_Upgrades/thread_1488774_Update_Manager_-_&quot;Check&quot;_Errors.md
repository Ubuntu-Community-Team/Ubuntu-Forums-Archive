---
title: "Update Manager - &quot;Check&quot; Errors"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by nshiell on 2010-05-20
Hi, I'm running Ubuntu 9.04 and when I goto "Update Manager" and click on "Check" I get The following error: -



```
]W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://download.virtualbox.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/jaunty/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Any ideas?

---

### Post by MonsterDigital on 2010-05-20
Hi... I hope you can understand me... i don't speak english... only i read a little... anyway... 

The problem's cause seems be change of repositories key public... 

And for me... works:

```

wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -

```

See you later... i really hope that I will help you...

bye...

---

### Post by lotus49 on 2010-05-22
Thank you for that.  I understood what you wrote and it was very helpful.  It worked for me too.

---

### Post by MonsterDigital on 2010-05-25
> **lotus49 said:**
> Thank you for that.  I understood what you wrote and it was very helpful.  It worked for me too.

Hi... you're welcome!, xD... 

That's great!!!... see you later...

:guitar:

---

### Post by 7@m3 G33k on 2010-05-26
@MonsterDigital: Worked for me too - thanks for the explanation and the code :-D

---

### Post by cchi on 2010-06-04
worked for me too, thanks!

---

### Post by MonsterDigital on 2010-06-12
> **7@m3 G33k said:**
> @MonsterDigital: Worked for me too - thanks for the explanation and the code :-D

> **cchi said:**
> worked for me too, thanks!

You're welcome... and thank's for posting... 

Good luck both... see you later...

Chao..

:guitar:

---

### Post by A_M_S on 2010-07-04
It also worked for me

Tnx!

---

### Post by danyd on 2010-07-28
See also [http://linux.aldeby.org/update-virtualbox-signing-key-54422a4b98ab5139.html](http://linux.aldeby.org/update-virtualbox-signing-key-54422a4b98ab5139.html)

In short enter command:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 54422A4B98AB5139
```

---

