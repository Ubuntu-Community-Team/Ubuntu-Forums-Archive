---
title: "Repository Select OK but D/L Error[s]"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by srose11 on 2011-05-11
I have Ubuntu 10.10 with several working kernels from 2.6.36 to.38. *** ALL 64 BIT ***.

Everything Works Great except now my Repository & Updates Do not Work.

There is a RED Error Button top right of the GNOME Panel...

I can select Repositories but than I get the Following Errors & am unable to Update...

Please let me know of any solutions...

Error Box / Message #1...

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
*****************************************************************

Error Box / Message #2...

E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/mozillateam-firefox-stable-maverick.list
E: Unable to lock the list directory
*****************************************************************

Error Box / Message #3...

E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/mozillateam-firefox-stable-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
*****************************************************************

Thanks for your suggestions / help :)

---

### Post by coffeecat on 2011-05-11
I can help you with errors #2 and #3. You have a malformed line in your /etc/apt/sources.list.d/mozillateam-firefox-stable-maverick.list file. Open a terminal and post the output of this command:

```
cat /etc/apt/sources.list.d/mozillateam-firefox-stable-maverick.list
```We will be able to see what's wrong with line 1 and then someone will be able to show you how to edit that file so that you don't get the error.

As far as error #1 is concerned, I think you've left an important bit out. There would have been a line or two telling us what the repository is that it cannot contact. The information is usually in the form of an URL. Was that message from a popup window or were you running apt-get in the terminal? If it was not from the terminal and from a popup window and there was no further information, run this from a terminal and post the output:

```
sudo apt-get update
```

---

### Post by srose11 on 2011-05-11
Messages were from a pop up box...

cat /etc/apt/sources.list.d/mozillateam-firefox-stable-maverick.list...output...>

ain


*****************************************************************

sudo apt-get update...output...>

E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/mozillateam-firefox-stable-maverick.list
E: The list of sources could not be read.

Now I can see and select any Repository even a speedtest for the fastest one but after I select my choice or even the Main Server I keep getting the same error messages above.

I can access Internet from same Ubuntu system with browsers etc no problem.

---

### Post by ajgreeny on 2011-05-11
The file /etc/apt/sources.list.d/mozillateam-firefox-stable-maverick.list is obviously either corrupted in some way or was recently made incorrectly.  All it seems to contain is "ain" whereas it should have a repository address.

Whichever it is, the file is useless and you might as well simply delete it with ```
sudo rm /etc/apt/sources.list.d/mozillateam-firefox-stable-maverick.list
```then run ```
sudo apt-get update
```

---

### Post by srose11 on 2011-05-11
Excellent :)

Fixed / Solved.

Thank You Very Much! I can now upgrade to Unity :))

---

### Post by coffeecat on 2011-05-11
> **ajgreeny said:**
> The file /etc/apt/sources.list.d/mozillateam-firefox-stable-maverick.list is obviously either corrupted in some way or was recently made incorrectly.  All it seems to contain is "ain" whereas it should have a repository address.

It's strange, isn't it? That's the second time I've seen a thread where the OP has the word "ain" in a corrupted ppa *.list file. I wonder who ain is? :-k

:wink:

---

### Post by srose11 on 2011-05-11
ain lol :)

Would u be able to help with a Wifi trouble shoot?

Marvell Wifi RTL8101e Not Working 10.10
I have Ubuntu 10.10 with several working kernels from 2.6.36 to.38. *** ALL 64 BIT ***.

Everything Works Great except Wifi, which I cannot get to work.

Apparently the drivers are in the kernel.

Here is the output for lspci the Ethernet Adapter(s) part...

Please let me know of any solutions...

08:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 03)
Subsystem: Marvell Technology Group Ltd. Device 2a08
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 32 bytes
Interrupt: pin A routed to IRQ 11
Region 0: Memory at f0210000 (32-bit, non-prefetchable) [size=64K]
Region 1: Memory at f0200000 (32-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>

0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
Subsystem: Gateway 2000 Device 0566
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 32 bytes
Interrupt: pin A routed to IRQ 43
Region 0: I/O ports at a000 [size=256]
Region 2: Memory at f0300000 (64-bit, non-prefetchable) [size=4K]
[virtual] Expansion ROM at ffce0000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: r8169
Kernel modules: r8169

---

### Post by ajgreeny on 2011-05-11
Could that happen if medibuntu servers are down when the command is run to add the repos?  I would have expected a more normal error, and still have no idea why "ain", but I am aware that every so often medibuntu repos go down and errors appear when refreshing the repository lists with ```
sudo apt-get update
```

---

### Post by srose11 on 2011-05-11
Yes Thanks the Repository problem was fixed as above...

But I have a Wifi problem as detailed, any suggestions?...

Marvell Wifi RTL8101e Not Working 10.10
I have Ubuntu 10.10 with several working kernels from 2.6.36 to.38. *** ALL 64 BIT ***.

Everything Works Great except Wifi, which I cannot get to work.

Apparently the drivers are in the kernel.

Here is the output for lspci the Ethernet Adapter(s) part...

Please let me know of any solutions...

08:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 03)
Subsystem: Marvell Technology Group Ltd. Device 2a08
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 32 bytes
Interrupt: pin A routed to IRQ 11
Region 0: Memory at f0210000 (32-bit, non-prefetchable) [size=64K]
Region 1: Memory at f0200000 (32-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>

0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
Subsystem: Gateway 2000 Device 0566
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 32 bytes
Interrupt: pin A routed to IRQ 43
Region 0: I/O ports at a000 [size=256]
Region 2: Memory at f0300000 (64-bit, non-prefetchable) [size=4K]
[virtual] Expansion ROM at ffce0000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: r8169
Kernel modules: r8169

---

