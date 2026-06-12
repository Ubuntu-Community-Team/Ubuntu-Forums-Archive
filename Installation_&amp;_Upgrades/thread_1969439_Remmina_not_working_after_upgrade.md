---
title: "Remmina not working after upgrade"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by kszys on 2012-04-30
I upgraded from 11.10 to 12.04 - everything is pretty much fine except for Remmina, which is not able to connect to anything... :mad:

I have a few RDP connections defined (to both Linux and Windows servers). They work fine with the Remote Desktop Client, but not with Remmina... Remmina always reports: "Unable to connect to RDP server [IP]".

Any clues anybody?

---

### Post by sforces on 2012-05-02
Running 12.04 64bit and same problem here. I noticed that I'm missing the RDP plugin in Tools>Plugins. And when I start from terminal I see it complaining that it can't find the RDP plugin even though the remmina-plugin-rdp is installed and ```
remmina-plugin-rdp.so is in /usr/lib/remmina/plugins
```

---

### Post by collisionystm on 2012-05-02
I would re-install remmina. I run 12.04 64 bit and have had 1 problem with rdp to windows servers.

That problem is I cannot connect with 32bit color, only 24. used to be able too.

---

### Post by sforces on 2012-05-02
Tried reinstalling. Have same issue on two systems now. Both upgraded to 12.04 64bit. One a desktop, one a laptop. ](*,)

> **collisionystm said:**
> I would re-install remmina. I run 12.04 64 bit and have had 1 problem with rdp to windows servers.

That problem is I cannot connect with 32bit color, only 24. used to be able too.

---

### Post by omriasta on 2012-05-02
Remmina not working for me too.
Some of my connections are OK but most of them just show a black window. Also on 12.04 64 bit
Edit:
Just noticed if I maximize the window I can see the remote desktop, unmaximizing after doesn't break it either.

---

### Post by collisionystm on 2012-05-02
do you see 

remmina-plugin-rdp.so

in 

/usr/lib/remmina/plugins

?

---

### Post by sforces on 2012-05-02
Yes, see my original post. :) But it still complains that it can't load it.

When loading from terminal, the exact message is:

```
Failed to load plugin: /usr/lib/remmina/plugins/remmina-plugin-rdp.so.
Remmina plugin VNC (type=Protocol) registered.
Remmina plugin VNCI (type=Protocol) registered.
Remmina plugin SFTP (type=Protocol) registered.
Remmina plugin SSH (type=Protocol) registered.
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)
Plugin not found (type=0, name=RDP)

```

> **collisionystm said:**
> do you see 

remmina-plugin-rdp.so

in 

/usr/lib/remmina/plugins

?

---

### Post by kszys on 2012-05-04
Well, in my case, this is happening on 32bit version. I tried to run remmina from command line:

```

$ remmina -c .remmina/1324540368496.remmina 
Remmina plugin RDP (type=Protocol) registered.
Remmina plugin RDPF (type=File) registered.
Remmina plugin RDPS (type=Preference) registered.
Remmina plugin VNC (type=Protocol) registered.
Remmina plugin VNCI (type=Protocol) registered.
Remmina plugin SFTP (type=Protocol) registered.
Remmina plugin SSH (type=Protocol) registered.
connected to 192.168.144.1:3386

```

This looks promising, but still a pop-up shows the same error: Unable to connect to RDP server 192.168.144.1 :( 

BTW: I connect to VMs run under VirtualBox on that server. As I said before, the connection using the Remote Desktop Client works fine.

---

### Post by kszys on 2012-05-09
A little update after (a lot) of experimentation:

It appears that the problem is somehow related to the version of the RDP server. The problem manifested itself, when I tried to access machines running on VirtualBox 4.0.16 and using the VRDP server of VirtualBox. This still does not work. 

However, when I created new VMs on another machine using VirtualBox 4.1.12, Remmina is able to connect to it without any problems. 

Also, I confirmed that the problem seems to be related to the FreeRDP libreries, as if I tried to use good old Remote Desktop Client (which does not use FreeRDP libraries), it can connect to both the old and new VirtualBox machines. 

Hence, the solution appears to be in my case to upgrade VirtualBox. :)

---

### Post by freakalad on 2012-05-11
I have/had exactly the same problem on a new 12.04 install on 32- & 64-bit OS.
Seems related to dependencies - possibly the RDP protocol.

I've been able to load remmina OK from another host over remote-X OK (`ssh -XCv $USER@$REMOTEHOST:/usr/bin/remmina`), so I'm not exactly sure what the root cause could be (gdb & strace is not helping much).

I've made a bug-report; I would urge you all add your 2c to bump attention to the issue: 
[https://sourceforge.net/tracker/?func=detail&aid=3522685&group_id=278330&atid=1181674](https://sourceforge.net/tracker/?func=detail&aid=3522685&group_id=278330&atid=1181674) 

UPDATE: on a whim I tried it again today - launched OK, but can't honestly say if it'll still work tomorrow.
ANOTHER UPDATE: after a reboot the problem is back. CLI launch craches with:
> 
$ remmina 
Remmina plugin GKEYRING (type=Secret) registered.
NX: detected keyboard type pc105/za
Remmina plugin NX (type=Protocol) registered.
Remmina plugin RDP (type=Protocol) registered.
Remmina plugin RDPF (type=File) registered.
Remmina plugin RDPS (type=Preference) registered.
Segmentation fault (core dumped)


---

### Post by freakalad on 2012-05-11
Found the cause to the bug!
Relates to a keyboard locale retting.

* [https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/794415](https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/794415)

Changing my keyboard to US seems to fix the problem

---

### Post by Phyrexicaid on 2012-05-13
> **freakalad said:**
> Found the cause to the bug!
Relates to a keyboard locale retting.

* [https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/794415](https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/794415)

Changing my keyboard to US seems to fix the problem

This doesn't fix all instances.  For my connections I deleted any saved passwords, and installed remmina-plugin-gnome.

I was then prompted to enter a password when connecting, and was then able to connect.

---

### Post by yanliu on 2012-08-16
After an upgrade several days ago, my remmina no longer worked. I kept getting following error:
SSL_read: Failure in SSL library (protocol error?)
Authentication failure, check credentials.
If credentials are valid, the NTLMSSP implementation may be to blame.

I tried the following and it solved the problem. Hopefully it's useful for others with the same problem:
- clear domain name or password in connection setting
- save and connect; input password and domain name again; then conn works well
- disconnect; and re-input password and domain name; then save

---

### Post by fisherking on 2012-10-12
Had the same problem, but changed "Security" under the Advanced tab *FROM* "Negotiate" *TO* TLS, and it worked ... for me anyway!

---

### Post by mha109 on 2012-11-16
The same as yanliu did, but I set the security to "RDP" instead of "Negotiate". Worked for me.

---

### Post by lvanderree on 2013-01-03
Thanks setting it to RDP did it for me as well!

---

### Post by senor_jt on 2013-03-29
Yep, thanks again for Negotiation --> RDP tip.   My Remmina connections to SBS 2008 boxes stopped working after some updates a while ago and this fixed it.  Thank you for sharing!

---

### Post by r_avital on 2013-07-03
Clean install of 12.04 LTS, 64Bit, remmina will not start.  At all.  Running from terminal produces this:

```
Remmina plugin XDMCP (type=Protocol) registered.
Remmina plugin telepathy (type=Entry) registered.
Remmina plugin GKEYRING (type=Secret) registered.
NX: detected keyboard type pc105/us
Remmina plugin NX (type=Protocol) registered.
Remmina plugin VNC (type=Protocol) registered.
Remmina plugin VNCI (type=Protocol) registered.
Remmina plugin RDP (type=Protocol) registered.
Remmina plugin RDPF (type=File) registered.
Remmina plugin RDPS (type=Preference) registered.
Remmina plugin SFTP (type=Protocol) registered.
Remmina plugin SSH (type=Protocol) registered.
Segmentation fault (core dumped)

```

Did some digging around, found the but related to the keyboard setting, so I checked /etc/default/keyboard (as specified in launchpad): 

```

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""
```

So my keyboard is us.  Doesn't solve the problem, still same output as above in terminal.

I've read the part about setting the security to RDP - how do I do that, if I can't start remmina at all?

Any thoughts?

Thanks in advance.

EDIT:
The above was all under gnome, Precise.  Did a complete purge, reinstalled remmina, didn't help, could not run it period.

Since this is a test box on my end, installed xubuntu, then I was able to run remmina, still got segmentation faults when connecting, and remmina crashed.  

Ran remmina from terminal.  A ton of parsing errors and gtk assertion failure errors came up, but it ran.  Followed the instructions above to change security to RDP in the "Advanced" tab, connected successfully.

xubuntu, this is the start of a beautiful friendship.

---

### Post by MiklinMA on 2013-12-23
[COLOR=#333333][FONT=Helvetica]hi there [/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]i found and place my easy solution at [/FONT][/COLOR][http://www.mechanicalbear.ru/20131223](http://www.mechanicalbear.ru/20131223)

---

