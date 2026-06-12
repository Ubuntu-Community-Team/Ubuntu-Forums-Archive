---
title: "newly installed 12.04, but can NOT access to internet"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by awinw on 2012-05-01
after updating grub2 on 10.04, I can now login to 12.04,
but
12.04 can not access to internet

I usually used classic desktop , 
but in 12.04,  it is all different,
I can not find where to set up internet
please help 
thanks

---

### Post by darkod on 2012-05-01
The Network Manager has an icon on the top bar, on the right side. It usually looks like two arrows, up/down. There is the option Edit Connections where you can set up wired, wireless, etc.

Also, if you open the Unity dashboard (the top unity button with the ubuntu logo) and search for Network that should work too.

---

### Post by davidm49 on 2012-05-01
> **awinw said:**
> 
I can not find where to set up internet


Are you looking for Network Connections? You can find it in Preferences (which seems like a strange place, but there it is).

Can you give some more detail of your problem? Are you trying to connect by ethernet, wifi or what? Do you know how to read the output of ifconfig? Some users (myself included) have had problems using the internet even when connected, because of the way that 12.04 handles DNS. (There is a solution for that, but we don't yet know if that is your problem)

---

### Post by awinw on 2012-05-02
> **darkod said:**
> The Network Manager has an icon on the top bar, on the right side. It usually looks like two arrows, up/down. There is the option Edit Connections where you can set up wired, wireless, etc.

Also, if you open the Unity dashboard (the top unity button with the ubuntu logo) and search for Network that should work too.

  re-boot with  recovery mode  "Enable networks"
then have access to internet.
but  after  reboot, again NO access to internet. 
it said "you are offline" or "cable unplugged"

review system manager ...> network tools
under network status: information of router
it said trying to check network status, but errors occur:
 /bin/netstat netstat -rn -A inet -A inet6

 what does these words mean?
Do I have to reinstall 12.04?

---

### Post by Taeolas on 2012-05-03
I'm having a similar problem. Had Ubuntu 11 installed, and it was working fine. Let it upgrade to 12.04, and it says my network cable is disconnected.

Neither my WiFi nor Wired connection are working it seems where they both worked before. 

I have a Dell Inspiron 1720. (and I just got to work for the day so I won't be able to do any trouble shooting until I get home later today)

---

### Post by davidm49 on 2012-05-03
> **Taeolas said:**
> .. it says my network cable is disconnected.

Neither my WiFi nor Wired connection are working ..

What happens if you type a numeric address in your browser's address bar?

For example,  [http://74.125.45.106](http://74.125.45.106)  is Google's numeric address.

If you reach the expected site, there is no problem with your connection.

Ubuntu 12.04 introduced a new way to handle DNS, the system that translates a URL (such as [http://www.google.com](http://www.google.com)) into a numeric internet address (such as the one written above).

This change is causing problems for a lot of users.

You can fix it temporarily by editing /etc/resolv.conf .

I can give details, but first you have to find out whether this is your actual problem.

---

### Post by Taeolas on 2012-05-03
> **davidm49 said:**
> What happens if you type a numeric address in your browser's address bar?

For example,  [http://74.125.45.106](http://74.125.45.106)  is Google's numeric address.

If you reach the expected site, there is no problem with your connection.

Ubuntu 12.04 introduced a new way to handle DNS, the system that translates a URL (such as [http://www.google.com](http://www.google.com)) into a numeric internet address (such as the one written above).

This change is causing problems for a lot of users.

You can fix it temporarily by editing /etc/resolv.conf .

I can give details, but first you have to find out whether this is your actual problem.


When I was trying to get it active earlier, I ended up deleting both my wired and wireless connections.

When I try to add the Wired connection, it shows up, but doesn't activate as far as I can tell. 

When I try to add a Wireless connection, I don't know what to put in for what it's asking for. 

I'm stumped for how to go forward from here; other than reinstalling 11 which is very likely now.

---

### Post by darkod on 2012-05-03
Plug in the wired cable, and you can check if it receives an IP with:
ifconfig

Type that in terminal and it will give some info about the connections. It would also display info about wireless connection but if you deleted it, now it won't be there.

---

### Post by Taeolas on 2012-05-03
No luck it seems. All I see is the Local Loopback entry (lo). Nothing for the network card.

I did a USB run of 11 that I still had, and that one still picks up the network card no problem.

(It also handles the dual display no problem too; once I installed it, it couldn't see my external monitor; but I'll search/report that separately)

---

### Post by davidm49 on 2012-05-04
> **Taeolas said:**
> All I see is the Local Loopback entry (lo). 
> When I try to add the Wired connection, it shows up ... 

I assume that the second quote means you find a Wired connection listed when you open Preferences -> Network Connections. If that is true, you might find something helpful here.

In the terminal, type ```
ifconfig -a 
```

(That will list inactive interfaces as well as the active ones.)

If eth0 is listed, type ```
sudo ifup eth0 
``` and then ```
ifconfig eth0 
```

Look for something about "inet addr" in the output. It's usually on the second line, and the third line should have "inet6 addr".

>  it says my network cable is disconnected. 
We could help you more easily if you said what you mean by "it", and what you do to elicit this message from "it". I am guessing that "it" is your web browser. On most browsers, when the browser has sent out a request and received no reply, it posts a message about being offline and the cable possibly being unplugged. There are many other possible reasons (including DNS failure) for the non-appearance of a reply, but the message usually doesn't tell you that. That's why I keep harping on about DNS, a known cause of this behaviour in 12.04.

---

### Post by davidm49 on 2012-05-04
> **awinw said:**
> netstat -rn -A inet -A inet6 

This is a Linux command to display the kernel routing tables in numeric form, using both IPv4 and IPv6 protocols. The other part of the line you quote (/bin/netstat) is the address of that command in your file system (provided for the sake of anyone whose PATH has been messed up). The routing tables might be helpful at some point in solving your problem, but there are better places to start.

The best place to start is for you to answer a question that you have already been asked. Are you trying to use a Wired or Wireless connection? It will be much easier to get things working initially on a Wired connection, leaving the Wireless config for later. Can you plug an Ethernet cable into your computer? (If connecting directly to a modem, you might have to unplug and replug the modem's power supply.)

With the cable plugged in, open a Terminal and type in ```
ifconfig -a 
```

If the output contains a table for "eth0", see whether the second line of the eth0 table begins with "inet". If there is an "eth0" but no "inet", follow the further instructions in post #10, above.

---

### Post by Taeolas on 2012-05-04
> **davidm49 said:**
> I assume that the second quote means you find a Wired connection listed when you open Preferences -> Network Connections. If that is true, you might find something helpful here.

In the terminal, type ```
ifconfig -a 
```

(That will list inactive interfaces as well as the active ones.)

If eth0 is listed, type ```
sudo ifup eth0 
``` and then ```
ifconfig eth0 
```

Look for something about "inet addr" in the output. It's usually on the second line, and the third line should have "inet6 addr".


We could help you more easily if you said what you mean by "it", and what you do to elicit this message from "it". I am guessing that "it" is your web browser. On most browsers, when the browser has sent out a request and received no reply, it posts a message about being offline and the cable possibly being unplugged. There are many other possible reasons (including DNS failure) for the non-appearance of a reply, but the message usually doesn't tell you that. That's why I keep harping on about DNS, a known cause of this behaviour in 12.04.

By "It" I mean the OS itself. When I first start up, I get a message pop up on my desktop about the Network being disconnected. Same happens when I try to enable it from the icon up next to my volume control.

ifconfig -a didn't show any inactive connections. (Sorry had the wrong command on my mind there before)

When I go to the "Network COnnections" window, I see 5 tabs: Wired, Wireless, Mobile Broadband, VPN and DSL. (I'm on a Fibre connection). I go to Wired, and click Add, it gives me 4 tabs: Wired (for the MAC addresses), 802.1x Security, IPV4 Settings and IPv6 settings.

Device MAC Address has a pulldown arrow, but nothing shows up in there. 

Ubuntu 11 can see my network connections with no problem. But 12 seems to be offline no matter what I do. :(

---

### Post by davidm49 on 2012-05-04
> **Taeolas said:**
> I go to Wired, and click Add, it gives me 4 tabs: Wired (for the MAC addresses), 802.1x Security, IPV4 Settings and IPv6 settings.

So, before you click "Add", there is nothing in the box below "Name". Then, after you click "Add" and the new pane opens with the 4 tabs, is there anything in the "Connection name" box - something like "Auto Ethernet" or "Wired connection 1"? (When the pane opens, that box is probably highlighted, ready for editing.)

If there is nothing in that box, type in "Auto Ethernet", and make sure that there is a check mark for "Connect automatically". If there is nothing in the "MTU" box, type "automatic" there.

In fact, it would be a good idea to make the connection name "Auto Ethernet" even if there is something else there already.

The "Device MAC address" ought to populate automatically. If it doesn't, write in the MAC address of your computer's ethernet adapter, followed by a space and then "(eth0)". (Don't write the quotes, but do write the brackets.)

You might have to move the pane upwards(*) on your screen to show the bottom line, where there is a check box for "Available to all users" and boxes for "Cancel" and "Save". For the time being, make the connection available to all, and save the config without going into any of the other tabs. (There's a good chance that you will have to go into the "IPv4 Settings" tab, but that can be done later.)

(*)To move the pane upwards, place the cursor in a blank area of the pane, hold down Alt+left mouse, and move the mouse upwards.

After saving, this connection should still be there if you close and then re-open the Network Connections. You should also find some output for "ifconfig eth0".

---

### Post by davidm49 on 2012-05-05
@Taeolas:

I hate to bring this up, but - if Network Connections fails to find a MAC address for your adapter, maybe 12.04 lacks the driver that you need. It would be best to eliminate this possibility first, to avoid wasting time trying solutions that won't work.

awinw mentions (post #4 above) being able to connect in recovery mode. If that works, at least it means that the kernel includes the right driver.

I would suggest, after selecting "network ... Enable networking" in recovery mode, next select "root ... Drop to root shell prompt" and type "ifconfig".

If no eth0 appears either for "ifconfig" or for "ifconfig -a", it would unfortunately appear that 12.04 does not (yet) support your ethernet card. Somebody other than me might be able to help you investigate this further.

If you don't find out anything that helps, you might do best to return to an earlier version of Ubuntu for the next few months, and then try again when support might be better.

On the other hand, if eth0 does appear with an inet address, try pinging Google's numeric address while you are still in root shell.```
ping 74.125.45.106 
```Press Ctrl+c to stop it after a short time - otherwise the ping will go on forever.

This will be really helpful in pointing the way to get you fully connected.

---

### Post by Taeolas on 2012-05-05
Thanks for all the help you've offered. I haven't solved the problem, but I reinstalled 11 for now and I'll wait longer for 12 to settle down a bit and hopefully I'll have a better solution then.

---

### Post by awinw on 2012-05-08
> **davidm49 said:**
> I assume that the second quote means you find a Wired connection listed when you open Preferences -> Network Connections. If that is true, you might find something helpful here.

In the terminal, type ```
ifconfig -a 
```(That will list inactive interfaces as well as the active ones.)

If eth0 is listed, type ```
sudo ifup eth0 
``` and then ```
ifconfig eth0 
```Look for something about "inet addr" in the output. It's usually on the second line, and the third line should have "inet6 addr".


We could help you more easily if you said what you mean by "it", and what you do to elicit this message from "it". I am guessing that "it" is your web browser. On most browsers, when the browser has sent out a request and received no reply, it posts a message about being offline and the cable possibly being unplugged. There are many other possible reasons (including DNS failure) for the non-appearance of a reply, but the message usually doesn't tell you that. That's why I keep harping on about DNS, a known cause of this behaviour in 12.04.

I repeat my scenario:

I had a wired connection 1 and my modem directly connected to desktop
on the same desktop there is 10.04 LTS working normally 
I installed 12.04  on a clean partition with live CD
then I can NOT access to internet (when I login to 12.04 desktoop)
the screen pop up warning "you are offline" "cable unplugged"  which is not the fact.
when I re-boot with recovery mode, I was able to login to online and make access to internet.

when I enter "Drop to root ..." terminal, and sudo ifconfig -a
here is the report:
  	 	 	 	 	 	   [FONT=AR PL UMing TW, serif][SIZE=4]~$ ifconfig -a[/SIZE][/FONT]
 

 [FONT=AR PL UMing TW, serif][SIZE=4]eth0      Link encap:Ethernet  HWaddr 00:80:c6:xx:xx:xx  [/SIZE][/FONT] 
 

           [FONT=AR PL UMing TW, serif][SIZE=4]inet6 addr: fe80::280:c6ff:xxxx:xxxx/64 Scope:Link[/SIZE][/FONT]
 

           [FONT=AR PL UMing TW, serif][SIZE=4]UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/SIZE][/FONT]
 

           [FONT=AR PL UMing TW, serif][SIZE=4]RX packets:8 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
 

           [FONT=AR PL UMing TW, serif][SIZE=4]TX packets:20 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
 

           [FONT=AR PL UMing TW, serif][SIZE=4]collisions:0 txqueuelen:1000 [/SIZE][/FONT] 
 

           [FONT=AR PL UMing TW, serif][SIZE=4]RX bytes:2101 (2.1 KB)  TX bytes:4171 (4.1 KB)[/SIZE][/FONT]
 

           [FONT=AR PL UMing TW, serif][SIZE=4]Interrupt:20 Base address:0xc000 [/SIZE][/FONT] 
 

 

 

 [FONT=AR PL UMing TW, serif][SIZE=4]lo        Link encap:Local Loopback  [/SIZE][/FONT] 
 

           [FONT=AR PL UMing TW, serif][SIZE=4]inet addr:127.0.0.1  Mask:255.0.0.0[/SIZE][/FONT]
 

           [FONT=AR PL UMing TW, serif][SIZE=4]inet6 addr: ::1/128 Scope:Host[/SIZE][/FONT]
 

           [FONT=AR PL UMing TW, serif][SIZE=4]UP LOOPBACK RUNNING  MTU:16436  Metric:1[/SIZE][/FONT]
 

           [FONT=AR PL UMing TW, serif][SIZE=4]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
 

           [FONT=AR PL UMing TW, serif][SIZE=4]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
 

           [FONT=AR PL UMing TW, serif][SIZE=4]collisions:0 txqueuelen:0 [/SIZE][/FONT] 
 

           [FONT=AR PL UMing TW, serif][SIZE=4]RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]-----------------[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]any body help please: How to read and understand these figures ???
[/SIZE][/FONT]

---

### Post by davidm49 on 2012-05-09
> **awinw said:**
>  

 [FONT=AR PL UMing TW, serif][SIZE=4]eth0      Link encap:Ethernet  HWaddr 00:80:c6:xx:xx:xx  [/SIZE][/FONT] 
 

           [FONT=AR PL UMing TW, serif][SIZE=4]inet6 addr: fe80::280:c6ff:xxxx:xxxx/64 Scope:Link[/SIZE][/FONT]
 

The "Ethernet HWaddr" is the code identifying the bit of hardware that connects to the outside world through your Ethernet cable. This is a good sign, as it means that your computer is recognizing that bit of hardware. (The hardware goes by various names, such as "Ethernet adapter", "network card", etc.)

Your output is interesting, because there is usually a line between the one beginning "eth0" and the one beginning "inet6". The missing line defines an internet address of the kind that most of us are still operating on (using a system called "IPv4" as opposed to the "IPv6" that we'll all eventually have to use).

It is possible (but unlikely) that your network has already switched over to IPv6 and stopped using IPv4. We can investigate that later, if we fail to connect you in IPv4.

Please now boot up 12.04 in the normal mode. Click on System -> Preferences -> Network Connections.

It should open on the "Wired" tab. Does it say anything in the box below "Name" (something such as"Wired connection 1" or "Auto Ethernet")? Whatever is there, click to highlight it, and then click "Edit" on the right-hand side.

A new window will open up. Click on the "IPv4 Settings" tab in the new window.

1. What is in the "Method" box? If it is something other than "Automatic (DHCP)", use the dropdown to change it to that.

2. Make sure that there are check marks in the boxes for  "Connect automatically" and "Available to all users".

3. Click "Save", enter your password when asked, and then close "Network Connections".

4. Open a terminal by pressing Ctrl+Alt+T and then type "ifconfig eth0" in the terminal.

5. See whether there is now a line of output beginning with "inet addr".

---

### Post by davidm49 on 2012-05-10
> **awinw said:**
> 
I had a wired connection 1 and my modem directly connected to desktop
on the same desktop there is 10.04 LTS working normally [FONT=AR PL UMing TW, serif][SIZE=4]
[/SIZE][/FONT]
[SIZE=2]
[SIZE=3][SIZE=2][EDIT: Just to make sure we are not wasting time here: are you plugged into a **cable** modem or a **DSL** modem? "Wired connection 1" is the connection you would configure for a cable modem. For a DSL modem, you need a different approach. If you are not sure what kind of modem you are using, follow the instructions below as far as point 7A, where you will find a way to determine whether or not you are using DSL.]

I am going to be away for a few days, so I had better tell you what to do next, if you have gone through[/SIZE][/SIZE] the procedure in post #17 and there is stlll no "inet addr" for the eth0 interface. This probably means that your network has some unusual feature, such as using static addresses instead of DHCP. Since everything works for you in Ubuntu 10.04, you can find the relevant details from that OS, if you follow the instructions below.

1. Boot up Ubuntu **10.04**.

2. Press Ctrl+Alt+T to open a terminal.

3. ```
ifconfig eth0 
```4. The second line of output will begin with "inet addr", followed by four numbers separated by dots. Write this down on a piece of paper. This is the IPv4 address that you are using in 10.04.

[EDIT: If there is no "inet addr" for eth0, maybe you are on a DSL connection. Continue as far as point 7A.]

5. ```
cat /etc/resolv.conf 
```6. The output will contain up to three lines beginning with "nameserver".
Write these lines down on the same piece of paper as before, making clear which one is the inet addr and which ones are nameserver. Keep the piece of paper safe for future reference.

7. Close the terminal. Open System -> Preferences -> Network Connections.

7A. To see whether you are using a DSL connection, click on the "DSL" tab. If there is nothing listed there under "Name", return to the "Wired" tab and continue with these instructions. On the other hand, if a connection is named on the "DSL" tab you will need a different approach than these instructions provide.

8. With luck, there will only be one connection listed on the "Wired" tab. Don't worry if it says "never" under the heading "Last Used". That's just a weird thing that sometimes happens. Highlight the connection name and click "Edit". (You are not actually going to change anything, but this is the only way to find out what is in there.)

9. A new window will open. Make notes of everything on the "Wired" tab and everything on the "IPv4 Settings" tab.

(There might be more than one Wired connection listed. That's another of those weird things. You are only interested in the one that has a MAC address. Ignore any others.)

10. Close the "Editing ..." window and the "Network Connections" window.

11. Reboot into Ubuntu 12.04.

12. Open Network Connections in 12.04.

13. Edit your Wired connection so that the IPv4 Settings are exactly the same as in 10.04.

14. Click on "Save" at the bottom of the Editing window, enter your password when asked, and close Network Connections.

15. Ctrl+Alt+T for a terminal, enter "ifconfig eth0", check for "inet addr".

16. If there is still no inet addr after doing everything in this post, I 'll have to tell you some more ifconfig commands to use with "sudo". This is enough for one post, though.
[/SIZE]

---

### Post by awinw on 2012-05-11
Davidm49:

I just tried these:

                        [FONT=AR PL UMing TW, serif][SIZE=4]1204 Recovery Mode [/SIZE][/FONT] 
 [FONT=AR PL UMing TW, serif][SIZE=4]desktop:~$ sudo ifconfig -a[/SIZE][/FONT]
 

[FONT=AR PL UMing TW, serif][SIZE=4]eth0      Link encap:Ethernet  HWaddr 00:80:c6.x.x[/SIZE][/FONT]          [FONT=AR PL UMing TW, serif][SIZE=4]inet addr:192.168.xx.xx  Bcast:192.168.1.255  Mask:255.255.255.0[/SIZE][/FONT]
          [FONT=AR PL UMing TW, serif][SIZE=4]inet6 addr: fe80::280.xxx.xxx:6846/64 Scope:Link[/SIZE][/FONT]
            [FONT=AR PL UMing TW, serif][SIZE=4]UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/SIZE][/FONT]


                         
[FONT=AR PL UMing TW, serif][SIZE=4]1004 normal[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]desktop:~$ sudo ifconfig -a[/SIZE][/FONT]

[FONT=AR PL UMing TW, serif][SIZE=4]eth0      Link encap:Ethernet  HWaddr 00:80:c6;x;x;x  [/SIZE][/FONT] 
            [FONT=AR PL UMing TW, serif][SIZE=4]inet addr:192.168.xx.xx  Bcast:192.168.1.255  Mask:255.255.255.0[/SIZE][/FONT]
            [FONT=AR PL UMing TW, serif][SIZE=4]inet6 addr: fe80::280;xxx;xxx:6846/64 Scope:Link[/SIZE][/FONT]



                           [FONT=AR PL UMing TW, serif][SIZE=4]1204 normal booting (NOT enable networking)[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]desktop:~$ sudo ifconfig -a[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]eth0      Link encap:Ethernet  HWaddr 00:80:c6;x;x;x  [/SIZE][/FONT] 
            [FONT=AR PL UMing TW, serif][SIZE=4]inet6 addr: fe80::280;xxx;xxx:6846/64 Scope:Link[/SIZE][/FONT]
---------------------------------------------

                          [FONT=AR PL UMing TW, serif][SIZE=4]1204 without enabling networking (normal boot)
[/SIZE][/FONT]
 [FONT=AR PL UMing TW, serif][SIZE=4]wired connection 1  >edit[/SIZE][/FONT]
 [FONT=AR PL UMing TW, serif][SIZE=4]wired connection 1: has machine code[/SIZE][/FONT]
 [FONT=AR PL UMing TW, serif][SIZE=4]IPv4: blank[/SIZE][/FONT]
  [FONT=AR PL UMing TW, serif][SIZE=4]IPv6: blank[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]*1204 and 1004 use the same hardware PC.
[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]--------------------[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]1204 Recovery Mode[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]wired connection 1  >edit[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]wired connection 1: has machine code[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]IPv4: auto DHCP[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]IPv6: auto[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]*thus 1204 and 1004 have same codes and settings.
[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]----------------------[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]both 12.04 Recoery Mode and 12.04 normal boot[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]DSL: blank[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]---------------[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]I hope these readings can help explain my scenario.

one more question:
how to add IPv4 into 12.04 networks settingS?
[/SIZE][/FONT]
[FONT=AR PL UMing TW, serif][SIZE=4]
[/SIZE][/FONT]

---

### Post by davidm49 on 2012-05-13
OK. Now, when you boot into 12.04 without using recovery mode, and then you look at the icons in the top right corner of the screen, what do you see just to the right of the little envelope? Does it look like waves radiating upwards?  There might be a line through the icon, as if to cross it out.
 
If you see something like that, right click on it. Some lines of writing should appear.
 
Is there a line saying "Enable networking"? If you find that line, left click on it. Does a check mark appear beside "Enable networking" when you do that? If so, that might be all you have to do.
 
If this does not succeed, please answer all of the questions in this post. For example, if you find up-and-down arrows instead of upward waves beside the little envelope, please say so in your reply.

---

### Post by awinw on 2012-05-14
> **davidm49 said:**
> OK. Now, when you boot into 12.04 without using recovery mode, and then you look at the icons in the top right corner of the screen, what do you see just to the right of the little envelope? Does it look like waves radiating upwards?  There might be a line through the icon, as if to cross it out.
 
If you see something like that, right click on it. Some lines of writing should appear.
 
Is there a line saying "Enable networking"? If you find that line, left click on it. Does a check mark appear beside "Enable networking" when you do that? If so, that might be all you have to do.
 
If this does not succeed, please answer all of the questions in this post. For example, if you find up-and-down arrows instead of upward waves beside the little envelope, please say so in your reply.
1)
 boot into 12.04 without using recovery mode, the icons.... look like waves radiating upwards?  
Yes, it more looks like vacant shell. Thus, off-line: no access to internet !
but,  check mark already appear beside "Enable networking" ( I  test click it off and on, still off-line)
2)
When  boot in with recovery mode,  instead I find up-and-down arrows instead of upward waves ,  then I can access to internet ! (and repeat do-loop 1) and 2) )
(right-click up-down arrows, there is  "network information" with MAC, Mask, MTU, DNS, IP...)

---

### Post by davidm49 on 2012-05-16
> **awinw said:**
>                         


                          [FONT=AR PL UMing TW, serif][SIZE=4]1204 without enabling networking (normal boot)
[/SIZE][/FONT]
 [FONT=AR PL UMing TW, serif][SIZE=4]wired connection 1  >edit[/SIZE][/FONT]
 [FONT=AR PL UMing TW, serif][SIZE=4]wired connection 1: has machine code[/SIZE][/FONT]
 [FONT=AR PL UMing TW, serif][SIZE=4]IPv4: blank[/SIZE][/FONT]
  [FONT=AR PL UMing TW, serif][SIZE=4]IPv6: blank[/SIZE][/FONT] 

On the IPv4 tab, does the "Method" box offer a drop-down menu if you click on the right-hand end of it. If so, select "Automatic (DHCP)" and then Save. If this is not possible, you could try typing in "Automatic (DHCP)" and then click on Save.

This ought to be the default after installation and then your connection should just work when you plug in the cable. If the Network Connections won't accept the attempts in the previous paragraph, it looks as though something went wrong with the installation.

At this point, you need to consider how much more work you want to do on this installation, rather than either (a) repeating the installation with your existing CD or USB medium or (b) waiting until 12.04 LTS comes out in a few months' time, with the worst bugs all fixed.

I can give you a terminal command that might give you internet access, using the information you have obtained from 10.04, to specify an IPv4 address and netmask for 12.04.

This is the info you have found for 10.04:
> eth0 Link encap:Ethernet HWaddr 00:80:c6;x;x;x 
inet addr:192.168.xx.xx Bcast:192.168.1.255 Mask:255.255.255.0 

Using the same numbers that you have represented above by xx.xx in the inet addr, enter this command in a terminal in 12.04: ```
sudo ifconfig eth0 192.168.xx.xx netmask 255.255.255.0 up 
```

(It is also possible to specify a default gateway, but I hope that won't be necessary, as it would involve consulting the routing table used in 10.04.)

Even if this works, you will have to do it again every time you reboot. It is possible to make a permanent change by editing /etc/network/interfaces , but it is also possible to screw things up in a major way. Until you have more experience with Linux, it is better to leave /etc/network/interfaces alone.

All things considered, you might find it best either to repeat the installation or to wait for 12.04 LTS, as suggested above.

---

### Post by jtarin on 2012-05-16
Unless I have comepletly overlooked it.....I have not seen in this thread any statement by the threadstarter "exactly" what kind of wired connection he has...."cable" or "Adsl"?

---

### Post by davidm49 on 2012-05-16
> **jtarin said:**
> Unless I have comepletly overlooked it.....I have not seen in this thread any statement by the threadstarter "exactly" what kind of wired connection he has...."cable" or "Adsl"?

You are right. I just assumed that he/she would notice and mention any ppp0 output from ifconfig when connected successfully in Ubuntu 10.04 (if such output existed), contrasted with the absence of ppp0 in non-connecting 12.04.

Where an explicit question (as in post #18 ) has gone unanswered, I have tried to deduce the  situation from the info available. If this does not help the threadstarter, he/she will maybe learn something nevertheless.

---

### Post by awinw on 2012-05-19
> **davidm49 said:**
> You are right. I just assumed that he/she would notice and mention any ppp0 output from ifconfig when connected successfully in Ubuntu 10.04 (if such output existed), contrasted with the absence of ppp0 in non-connecting 12.04.

Where an explicit question (as in post #18 ) has gone unanswered, I have tried to deduce the  situation from the info available. If this does not help the threadstarter, he/she will maybe learn something nevertheless.

I appreciated your answers and comments all these days.
I now solved the networking headaches:

First,  remove PAE from 12.04 LTS
        In the meanwhile, I installed a 12.04 mini.iso on a new partition,
        both ways work!
Secondly, modify /etc/network/interfaces and /etc/networkmanager/networkmanager.conf

thus I can surf on internet, youtube, ...

thanks.

---

