---
title: "[SOLVED] LTS failed to update AGAIN!"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by jim_p on 2007-09-06
Today, I did the regular manual update of my system.
By manual I mean this
```
sudo apt-get update && sudo apt-get upgrade
```

And I got some errors... 19 to pe precise but with a common layout!

```
&#931;&#966;&#940;&#955;&#956;&#945; ftp://ftp.ntua.gr dapper/main Packages
  &#913;&#948;&#965;&#957;&#945;&#956;&#943;&#945; &#955;&#942;&#968;&#951;&#962; &#964;&#959;&#965; &#945;&#961;&#967;&#949;&#943;&#959;&#965;, &#959; &#948;&#953;&#945;&#954;&#959;&#956;&#953;&#963;&#964;&#942;&#962; &#945;&#960;&#940;&#957;&#964;&#951;&#963;&#949; 'No such file.  ' [IP: (some ip out there) ]

---Translation

Error ftp://ftp.ntua.gr dapper /main Packages
  Unable to receive file, the server responded 'No such file.  ' [IP: (some ip out there) ]

```

Now I am worried!!!

This happens for all 19 errors in the same manner
Only the words  "dapper /main" change as it goes on.

These are the active repos I have in my sourses.list
```

deb ftp://ftp.ntua.gr/ubuntu/ dapper main restricted universe multiverse
deb ftp://ftp.ntua.gr/ubuntu/ dapper-updates main restricted universe multiverse
deb ftp://ftp.ntua.gr/ubuntu/ dapper-backports main restricted universe multiverse
deb ftp://ftp.ntua.gr/ubuntu/ dapper-security main restricted universe multiverse
deb ftp://ftp.ntua.gr/ubuntu/ dapper-proposed main restricted universe multiverse

```
and I use the ftp.ntua.gr server because I am Greek (localization reasons) and it gives me the lowest ping of all (~25ms)
Note that I get the all the "Release" files and all the .gpg files from the server
And I know it is up cause it responds to ping.

Please, help me before I bang my head on the screen!

---

### Post by lcg on 2007-09-06
> **jim_p said:**
> Today, I did the regular manual update of my system.
By manual I mean this
```
sudo apt-get update && sudo apt-get upgrade
```

And I got some errors... 19 to pe precise but with a common layout!

```
&#931;&#966;&#940;&#955;&#956;&#945; ftp://ftp.ntua.gr dapper/main Packages
  &#913;&#948;&#965;&#957;&#945;&#956;&#943;&#945; &#955;&#942;&#968;&#951;&#962; &#964;&#959;&#965; &#945;&#961;&#967;&#949;&#943;&#959;&#965;, &#959; &#948;&#953;&#945;&#954;&#959;&#956;&#953;&#963;&#964;&#942;&#962; &#945;&#960;&#940;&#957;&#964;&#951;&#963;&#949; 'No such file.  ' [IP: (some ip out there) ]

---Translation

Error ftp://ftp.ntua.gr dapper /main Packages
  Unable to receive file, the server responded 'No such file.  ' [IP: (some ip out there) ]

```

Now I am worried!!!

The FTP server told you exactly what was wrong ...

> **jim_p said:**
> These are the active repos I have in my sourses.list
```

deb ftp://ftp.ntua.gr/ubuntu/ dapper main restricted universe multiverse
deb ftp://ftp.ntua.gr/ubuntu/ dapper-updates main restricted universe multiverse
deb ftp://ftp.ntua.gr/ubuntu/ dapper-backports main restricted universe multiverse
deb ftp://ftp.ntua.gr/ubuntu/ dapper-security main restricted universe multiverse
deb ftp://ftp.ntua.gr/ubuntu/ dapper-proposed main restricted universe multiverse

```
and I use the ftp.ntua.gr server because I am Greek (localization reasons) and it gives me the lowest ping of all (~25ms)

<irony>Yeah, and latency is extremely important when you're updating your system.</irony>

Seriously, have you had a look at [ftp://ftp.ntua.gr/](ftp://ftp.ntua.gr/) ? When I tried [ftp://ftp.ntua.gr/ubuntu/](ftp://ftp.ntua.gr/ubuntu/), it told me that it couldn't change to that directory.
This isn't really that surprising since there is only a directory /pub, not a /ubuntu. So it seems that the server admin changed the directory layout.

> **jim_p said:**
> 
Note that I get the all the "Release" files and all the .gpg files from the server


Now that surprises me. Since there is no /ubuntu on that FTP server as your sources.list claims there to be, those files should give you an error as well.

> **jim_p said:**
> 
And I know it is up cause it responds to ping.


Yes, the box and the FTP server is up, but the data you are looking for is not where you are looking for it.

HTH,
Lars

---

### Post by jim_p on 2007-09-06
>  <irony>Yeah, and latency is extremely important when you're updating your system.</irony> 

You can call me stupid, but updating from the default server, which gives me higher ping, takes more time.
Besides I have no super fast connection to the net like most. 768kbps is what I have

Anyway, thank you for checking up the server.
It seems they are re-organizing it or simply removing ubuntu.
On that one and on the other greek one that I have :(
I have looked everywhere on these 2 for the correct path to update but no luck.
Guess I will update from the default server...

And excuse me for the hassle...
I am using this server since I first installed ubuntu last December, I have downloaded dozens of MB from there
and now... it fails :(

---

### Post by lcg on 2007-09-06
> **jim_p said:**
> You can call me stupid, but updating from the default server, which gives me higher ping, takes more time.
Besides I have no super fast connection to the net like most. 768kbps is what I have

I did not call you stupid. But as a matter of fact, bandwidth and latency are two different things. Sometimes the two are related as slower lines can cause a higher delay.

The latency (which you measure with 'ping') tells you how long it takes for a packet to arrive at the receiver's end. Bandwidth OTOH is a measure for how many packets (=how much data) you can send or receive in a certain time. So technically, you could have a connection which delays packets for several seconds and still reach a bandwidth of 1Gbit/s or more.

Latency is usually an interesting number in online games since it determines how long status updates travel between your box and the server. But if you want to download packages, you usually don't care whether a packet takes 25ms or 1s to arrive at your end of the connection. It's more important that a lot of packets arrive in a short period of time.

HTH,
Lars

---

### Post by jim_p on 2007-09-07
The ntua.gr repository is up again. I was this close to sending a complaint email 
Life smiles to me again :)

I understand your explaination for the differences between ping and bandwidth
>  It's more important that a lot of packets arrive in a short period of time 

I think that a server with the huge 100MBps bandwidth will spare a tiny 0.768MBps for me to do my job :)

---

