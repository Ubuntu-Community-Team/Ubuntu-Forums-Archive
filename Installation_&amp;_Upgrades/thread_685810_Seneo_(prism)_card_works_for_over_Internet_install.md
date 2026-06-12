---
title: "Seneo (prism) card works for over Internet installation but not after reboot -Xubuntu"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by oregonvet on 2008-02-02
Okay, I'm trying to salvage an old Thinkpad 240 with a 300 celeron and 128 RAM and 6 gig HDD. The problem is there is no internal CD. So through windows I went to a website that began the installation from within windows. It took over the system, downloaded everything needed and went through installation without any problems wirelessly over a Seneo card which has worked great with live CDs on other laptops. But when it finally rebooted into xubuntu I couldn't get online. I've beat my head against the wall trying ndiswrapper but I keep getting an error when I go through the make function- missed directory somewhere. Thank you, kevdog for that thread. But before I start all over with that, I wanted to make sure that's the right road. My card lights up. But this it what I get with the following commands. The ssid is my own on from my router. 

oregonvet@240:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 03)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:09.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)
00:0a.0 CardBus bridge: Texas Instruments PCI1211
00:0b.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 02)
00:0c.0 Communication controller: Agere Systems WinModem 56k (rev 01)
oregonvet@240:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

eth0      IEEE 802.11b  ESSID:"ncc04101970-a?"  Nickname:""
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:30:BD:93:99:1D   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0_rename  IEEE 802.11b  ESSID:"ncc04101970-a?"  Nickname:""
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:30:BD:93:99:1D   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-35 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:727   Missed beacon:0

oregonvet@240:~$ ifconfig
eth0      Link encap:UNSPEC  HWaddr 00-02-6F-09-7A-49-40-E2-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:199 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:657808 (642.3 KB)  TX bytes:0 (0.0 b)
          Interrupt:4 Base address:0x180 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10100 (9.8 KB)  TX bytes:10100 (9.8 KB)

---

### Post by oregonvet on 2008-02-02
The rest:
oregonvet@240:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:30:BD:93:99:1D
                    ESSID:"ncc04101970-a"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Signal level=-34 dBm  Noise level=-97 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10

wlan0_rename  Scan completed :
          Cell 01 - Address: 00:30:BD:93:99:1D
                    ESSID:"ncc04101970-a"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Signal level=-58 dBm  Noise level=-99 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:resp_rate=10
Thank you for any help!

---

