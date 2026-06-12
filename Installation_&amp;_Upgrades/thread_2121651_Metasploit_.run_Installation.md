---
title: "Metasploit .run Installation"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by roffisserver on 2013-03-02
I am trying to install Metasploit(A Penetration Testing Framework). I when I download it is a .run file. How would I install this file?

---

### Post by haqking on 2013-03-02
> **roffisserver said:**
> I am trying to install Metasploit(A Penetration Testing Framework). I when I download it is a .run file. How would I install this file?

LOL, no offence but if you cant run a .run file you will have a experience to say the least using MSF especially in its preffered format which is the MSF CLI or MSFconsole.  You might want to learn some more Linux first.

Anyways a .run file is run as

```
sh ./file<name>.run
```

or

```
sudo ./<filename>.run
```

./ presumes you are in the files location.

If you want to learn and play with it you are better off downloading the BT 5 R3 .iso and playing with it in a VM or live CD as it is already configured.

If not then read this [http://www.darkoperator.com/installing-metasploit-in-ubunt/](http://www.darkoperator.com/installing-metasploit-in-ubunt/)

and the free offensive security course on it here [http://www.offensive-security.com/metasploit-unleashed/Introduction](http://www.offensive-security.com/metasploit-unleashed/Introduction)

---

### Post by roffisserver on 2013-03-02
I know quite a bit about Linux I just haven't come upon a .run file before.
                                                                
                                                                  Thanks

---

### Post by Atlantic777 on 2013-03-02
I think that you actually need to run that file with ./filename.run
It may work with sh filename.run but in case you get some executable script which isn't a bash script, you can get in troubles. The thing is that the first line of such scripts usually is something like #!/usr/bin/pythoon or #!/bin/sh which tells "the system" which interpreter to use. So chmod +x and just ./filename.run is maybe a better choice. :)

---

### Post by haqking on 2013-03-02
> **Atlantic777 said:**
> I think that you actually need to run that file with ./filename.run
It may work with sh filename.run but in case you get some executable script which isn't a bash script, you can get in troubles. The thing is that the first line of such scripts usually is something like #!/usr/bin/pythoon or #!/bin/sh which tells "the system" which interpreter to use. So chmod +x and just ./filename.run is maybe a better choice. :)

That is why I gave both options ;-)

Anyways to the OP you can read there instructions at their official docs here  [https://community.rapid7.com/docs/DOC-1293](https://community.rapid7.com/docs/DOC-1293)

and specifically for Ubuntu using the binary here [https://community.rapid7.com/docs/DOC-1296](https://community.rapid7.com/docs/DOC-1296)

---

