---
title: "Command line apt-get distribution upgrade possible?"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by dslowik2 on 2012-05-10
There must be a simple way to upgrade an Ubuntu distribution using apt-get commands on the command line (rather than using a gui). After reading the apt-get man page it seems that apt-get is a fairly sophisticated system, and that this is the kind of thing it was built for. For instance if I just alter the sources.list file to point to the new repositories, do an update, then upgrade?

The reason I'm asking is that when I use Update Manager, or follow the instructions for using an iso CD downloaded from the internet, the process becomes totally flummoxed in the layers of Python code called by the cdromupgrade executable;  it always goes back to the internet even though I tell it not to (I have a dial-up connection, AND I already downloaded the CD!)! It seems that all of that should not be required if I simply want to use apt-get to upgrade my distro...

Any help along these lines greatly appreciated.

PS I'm starting with Maverick (10.10)

---

### Post by zvacet on 2012-05-11
> For instance if I just alter the sources.list file to point to the new repositories, do an update, then upgrade?
Yes,you can do that,but I think it is not recommended way of upgrade.Since you are using 10.10 and having dial up it is long way to the 12.04.If you have separate home partition make fresh install of 12.04.If you don´t have separate home you can make on following [this]("http://www.psychocats.net/ubuntu/separatehome") guide.

---

### Post by jadtech on 2012-05-11
dail up online upgrade ?? takes nearly 2 hours on cable connection

keep in mind if  you disconnect  for even a split second or a packet drops it  may  or may not stop the down load or install on missed package will mess everything up completely maybe not toast but  could be a week or more working out the  details to get booting ..

---

### Post by billyseth on 2012-05-11
Yeah, agreed, a full distro upgrade is going to pull in ALOT of data which is going to take a long while. You also might be risking the connection dropping or some other sort of problem that could happen with such a long process, and would result in a botched install.

I would recommend playing it safe with the CD install

---

### Post by CharlesA on 2012-05-11
You can run the upgrade in screen just fine.

It will warn you not to do it over ssh and open another ssh session on a different port in case you get disconnected.

Note: As far as I know if is not possible to do an upgrade via CD, it will download the required packages and if you are on dialup, that will take a long, long time.

---

