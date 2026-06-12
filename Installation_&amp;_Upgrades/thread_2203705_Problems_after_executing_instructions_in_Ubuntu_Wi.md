---
title: "Problems after executing instructions in Ubuntu Wiki LTSEnablementStack"
date: 2014-02-04
forum: Installation &amp; Upgrades
---

### Post by achim_59 on 2014-02-04
In the process of trying to get a dongle working, (see [this thread]("http://ubuntuforums.org/showthread.php?t=2197164")) I performed an update in accordance with the instructions in [LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"). This allowed me to get a Nokia CS-15 working. However, I now have some other problems. Firstly, the Network manager doesn't start when I log in. Secondly, my [FONT=Courier New].profile[/FONT] doesn't appear to run when I log in. when I first check $PATH I get a different result to what I get when i run the [FONT=Courier New].profile[/FONT] explicitly:
```
achim@achim-W840SU-Series:~$ echo $PATH
/home/achim/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
achim@achim-W840SU-Series:~$ . .profile
achim@achim-W840SU-Series:~$ echo $PATH
/usr/local/share/ant/apache-ant-1.9.3/bin:/usr/local/share/jboss_7/jboss-as-7.1.1.Final/bin:/usr/local/share/java_se/jdk1.7.0_51/bin:/home/achim/bin:/home/achim/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

Thirdly, an update from the Update Manager gave me the following response:
> Requires installation of untrusted packages
Listing the details showed the following:
> libnautilus-extension1a linux-headers-3.11.0-15 
linux-headers-3.11.0-15-generic 
linux-headers-3.8.0-35 linux-headers-3.8.0-35-generic 
linux-image-3.11.0-15-generic linux-image-3.8.0-35-generic 
nautilus
nautilus-data 
There are a number of posts about similar problems. The one that seemed to be the most relevant is [this one]("http://ubuntuforums.org/showthread.php?t=2173022&highlight=Requires+installation+untrusted+packages"). The problem is that the solution not only involves an update, but also an **upgrade**. I do not want to upgrade, I want to stick with 12.04 LTS at least until the next LTS version is available or (maybe) until support for 12.04 runs out. I did the [FONT=Courier New]"sudo apt-get update"[/FONT] thing, so that might keep the Update Manager happy for a while, though looking at the output, I rather doubt it.

So 3 questions:
1. Will setting [FONT=Courier New]"managed = true"[/FONT] in NetworkManager.conf fix the problem with the network manager, so that I can again use a LAN or WLAN connection?
2. Why is my [FONT=Courier New].profile[/FONT] not being executed?
3. Is there any way to avoid having to do manual updates, since the Update Manager won't allow the "unsecure" updates?

**Additional Info:**
Something I forgot to mention is that at start-up the screen displays "Waiting for network configuration". It then waits for around 2 minutes before presenting me with the log-in screen.

---

### Post by achim_59 on 2014-02-05
Firstly, the network issue isn't as difficult as I thought... at leastnot for WLAN and Broadband. I changed the file " [FONT=Courier New]/etc/NetworkManager/NetworkManager.conf[/FONT] " so that " [FONT=Courier New]managed=true[/FONT]". The result is that sometimes networking starts after I log in and sometimes it doesn't. If it doesn't, I select System > Network and - presto! - NetworkManager starts.

Secondly, as expected the update manager made another appearance with some more updates in addition to the ones that didn't work before. Out of sheer perversity I clicked "install updates" and, surprise, it started downloading and installing all the updates without complaint. All I had done is, as mentioned previously, to enter " [FONT=Courier New]sudo apt-get update[/FONT] " on the console. Somehow this has fixed whatever was wrong.

The remaining difficulties still... well... remain. My  [FONT=Courier New].profile[/FONT]  does not get run when I log in. When I start the machine, it still comes up with "wating for network configuration" and waits for at least 2 minutes. 

If I solve these problems, then I'll post the answers. If anybody has a hint for me, I'd be happy to hear/read it.

---

### Post by achim_59 on 2014-02-06
I take it back. It is now more difficult than ever to get a stable connection.

I tried creating a launcher to force the network manager to start. It contained the following command:
```
gksu service network-manager restart
```

Since using this the dongle drops out after at most 2 or 3 minutes, sometimes almost immediately. I'm going to try to post this after starting the device again, if it stays up long enough.

Can somebody PLEASE help? I'm getting desperate. Could this be a hardware problem?

**Additional Info:**
Almost immediately after posting the stuff above, my connection dropped out again. Reconnecting was useless, because it dropped out again after a few seconds. I'm posting this edit with my old WinXP machine. However it also drops out without warning. Maybe the dongle is kaput?

---

### Post by achim_59 on 2014-02-16
I have come to the conclusion that my dongle is the problem (at least regarding the mobile Internet). I'm sending it back under guarantee and I'll have to buy a new one. 

The dongle problem is being dealt with in [another thread]("http://ubuntuforums.org/showthread.php?t=2197164&page=1"). The update manager problem has aparently fixed itself. That really only leaves the Network Manager issue and the fact that  [FONT=Courier New].profile[/FONT]  doesn't run automatically.

The Network Manager has settled down and is behaving in a predictable fashion now. When I have a LAN connection, the NM starts immediately and the boot-up takes only a few seconds. When I don't have a LAN connection I still get the "waiting for network configuration" message and the boot-up takes 2 minutes. WHY? This surely isn't normal.

My  [FONT=Courier New].profile[/FONT]  still doesn't run when I log-in. Here's the proof:
```
achim@achim-W840SU-Series:~$ echo $JAVA_HOME

achim@achim-W840SU-Series:~$ . .profile 
achim@achim-W840SU-Series:~$ echo $JAVA_HOME
/usr/local/share/java_se/jdk1.7.0_51
achim@achim-W840SU-Series:~$ 
```

I have checked  [FONT=Courier New]/etc/profile[/FONT]  and  [FONT=Courier New]/etc/profile.d/bash_completion[/FONT]  and found nothing untoward. There are a whole mess of scripts in  [FONT=Courier New]/etc/bash_completion.d[/FONT]  and I don't think it would be productive to go through then 1 by 1. I can execute the  [FONT=Courier New].profile[/FONT]  explicitly as seen above, but I'd be happier if it worked normally.

Any insights? Hmmm?? I don't expect answers, but a hint or two as to where I can look would be a start.

---

### Post by achim_59 on 2014-03-16
This is probably my last post on this subject, since I've had zero response.

There are oodles of posts out there about .profile not running under various circumstances. None of them seem relevant. The things explained in those posts (ad nauseum) are all things of which I am aware:
[LIST]
[*].profile is only sourced automatically for log-in shells.
[*].profile is not sourced if .bash_profile or .bash_login exist
[/LIST]
Neither of those tips get me any further... as mentioned, I knew that already.

As far as the networking problem is concerned, I take back the assertion that it works OK when the LAN cable is connected. Regardless of whether or not the macine is attached to a network or not, at log-in I get the message "waiting for network configuration". This is annoying, since the machine would otherwise boot up in about 15 seconds. As it is, I have to wait 2 minutes.

If I find a solution I'll post it... if the thread isn't closed first.

---

### Post by achim_59 on 2014-03-19
A work-around for the networking problem can be found [here]("http://tech.pedersen-live.com/2012/05/disable-waiting-for-network-configuration-messages-on-ubuntu-boot/"). I did this and now I get a short message saying the bootup will continue without full network configuration. This is fine by me, since it seems to make no difference whatever to the behaviour of the laptop. 

There is another solution at [this URL]("http://virtualboximages.com/%5BSolved%5D+Waiting+for+network+configuration.+Waiting+up+to+60+seconds+for+network+configuration"). I haven't tried that one and, since the work-around seems to work, I probably won't bother.

Never-the-less it is somewhat unsatisfying to have these solutions which say: "do this... edit that... and it will all workout." It would be really nice if somebody would expain what is really going on. Like, what is this "PLYMOUTH" thing? What does it do for networking? Does anybody know where I can find out?

For the sake of completeness, my /etc/network/interfaces file looks like this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface ppp0 inet ppp
provider ppp0

auto ppp0
```
Since that second solution recommends changing "eth0," I trien the command "ifconfig -a" to see if there wa anything amiss. here's what I got:
```
eth0      Link encap:Ethernet  HWaddr 00:90:f5:f0:73:f5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0:avahi Link encap:Ethernet  HWaddr 00:90:f5:f0:73:f5  
          inet addr:169.254.12.224  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85392 (85.3 KB)  TX bytes:85392 (85.3 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.50.137.159  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:10802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:11667941 (11.6 MB)  TX bytes:820309 (820.3 KB)

wlan0     Link encap:Ethernet  HWaddr 0c:8b:fd:6c:25:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wwan0     Link encap:Ethernet  HWaddr 0a:ef:75:5a:5d:44  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
Doesn't really help, so I'm sticking with the work-around.

---

