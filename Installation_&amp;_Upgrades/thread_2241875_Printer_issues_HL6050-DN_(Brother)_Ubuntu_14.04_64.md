---
title: "Printer issues HL6050-DN (Brother) Ubuntu 14.04 64"
date: 2014-08-28
forum: Installation &amp; Upgrades
---

### Post by xigen on 2014-08-28
I installed ubuntu 14.04 and now my printer is not working.

On prior occasions - the issue was that the UI to add a printer is incomplete and you need to use the command line:
$ system-config-printer

Brother has a website with support.  It is not good:
[HTML]http://support.brother.com/g/b/countrytop.aspx?c=us&lang=en#HL-6050D[/HTML]

Here is the output I get when I try to print a web page:

```
meow@MeowBatunde:~/Downloads$ ping 192.168.2.138
PING 192.168.2.138 (192.168.2.138) 56(84) bytes of data.
64 bytes from 192.168.2.138: icmp_seq=1 ttl=60 time=2.41 ms
64 bytes from 192.168.2.138: icmp_seq=2 ttl=60 time=1.24 ms
64 bytes from 192.168.2.138: icmp_seq=3 ttl=60 time=1.23 ms
64 bytes from 192.168.2.138: icmp_seq=4 ttl=60 time=1.25 ms
64 bytes from 192.168.2.138: icmp_seq=5 ttl=60 time=1.27 ms
64 bytes from 192.168.2.138: icmp_seq=6 ttl=60 time=1.25 ms
64 bytes from 192.168.2.138: icmp_seq=7 ttl=60 time=1.22 ms
64 bytes from 192.168.2.138: icmp_seq=8 ttl=60 time=1.23 ms
64 bytes from 192.168.2.138: icmp_seq=9 ttl=60 time=1.23 ms
^Z
[1]+  Stopped                 ping 192.168.2.138
meow@MeowBatunde:~/Downloads$ system-config-printer
Unknown value for media-col: (unknown IPP value tag 0x34)
Choices: [u'media-bottom-margin', u'media-left-margin', u'media-right-margin', u'media-size', u'media-source', u'media-top-margin', u'media-type']
Selecting from choices: media-bottom-margin
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 461 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
Unknown value for media-col: (unknown IPP value tag 0x34)
Choices: [u'media-bottom-margin', u'media-left-margin', u'media-right-margin', u'media-size', u'media-source', u'media-top-margin', u'media-type']
Selecting from choices: media-bottom-margin
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 1865 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 2909 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
Unknown value for media-col: (unknown IPP value tag 0x34)
Choices: [u'media-bottom-margin', u'media-left-margin', u'media-right-margin', u'media-size', u'media-source', u'media-top-margin', u'media-type']
Selecting from choices: media-bottom-margin
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 1877 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 3429 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 3610 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 3443 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
No ID match for device dnssd://Brother%20HL-6050D_DN%20series._printer._tcp.local/:
MFG:Brother;MDL:HL-6050D_DN series;CMD:PS,PCL;
No ID match for device dnssd://Brother%20HL-6050D_DN%20series._printer._tcp.local/:
MFG:Brother;MDL:HL-6050D_DN series;CMD:PS,PCL;
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 5102 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
Unknown value for media-col: (unknown IPP value tag 0x34)
Choices: [u'media-bottom-margin', u'media-left-margin', u'media-right-margin', u'media-size', u'media-source', u'media-top-margin', u'media-type']
Selecting from choices: media-bottom-margin
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 5142 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
Unknown value for media-col: (unknown IPP value tag 0x34)
Choices: [u'media-bottom-margin', u'media-left-margin', u'media-right-margin', u'media-size', u'media-source', u'media-top-margin', u'media-type']
Selecting from choices: media-bottom-margin
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 6662 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 6687 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 6938 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 6959 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 6970 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 6971 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 6980 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 7010 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 7026 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 7043 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 7046 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 7050 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 7057 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 7065 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 7069 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 7077 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 7082 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 7084 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 7090 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 7131 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 7140 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 7141 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 7150 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 7151 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 7157 was not found when attempting to remove it
  GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 7161 was not found when attempting to remove it
  GLib.source_remove (self.populateList_timer)
/usr/share/system-config-printer/monitor.py:190: Warning: Source ID 7172 was not found when attempting to remove it
  GLib.source_remove (timer)
```

I reset my router (just in case).

Any suggestions about what to do next?

---

### Post by xigen on 2014-08-29
Solved!

The device URI is required.  
for my printer the **URL is: 192.168.2.139  ** *obtained by going to the printer and printing out 'settings'
**making the URI: socket://192.168.2.138:9100**

Also, use:
[B]$ system-config-printer

Some stuff is (has been) missing from the menu UI. [/B]

I am at a complete loss as to why configuring my printer is soooo difficult.  

for now:  solved.

---

### Post by xigen on 2014-08-29
Well - it worked for a minute.

Now I am getting a message: error 508

Here is the output from the Brother install script: 
```

rm -f /usr/lib/cups/filter/brlpdwrapperHL6050D
 * Restarting Common Unix Printing System cupsd
   ...done.
#
Will you specify the Device URI? [Y/n] ->y


0: ipp14
1: ipps
2: http
3: ipp
4: socket
5: https
6: lpd
7: smb
8: serial:/dev/ttyS0?baud=115200
9: hp
10: hpfax
11: dnssd://Brother%20HL-6050D_DN%20series._printer._tcp.local/
12: lpd://BRN_3C811E/BINARY_P1
13 (I): Specify IP address.
14 (A): Auto. (dnssd://Brother%20HL-6050D_DN%20series._printer._tcp.local/)

select the number of destination Device URI. ->4

lpadmin -p HL6050D -v socket -E
lpadmin: Bad device-uri "socket".
Test Print? [y/N] ->y

wait 5s.
lpr -P HL6050D /usr/share/cups/data/testprint
Hit Enter/Return key.
```

---

### Post by xigen on 2014-08-29
It looks like there was a conflict between two installs of the printer.  Very strange.

I deleted one instance of the printer 
$ system-config-printer    .. remove printer

Then the printer worked again.

---

### Post by pdc on 2014-08-29
so did you select > [COLOR="#EE82EE"]dnssd://Brother%20HL-6050D_DN%20series._printer._tcp.local/[/COLOR] .................which was no. 11 in the options in the Brother install script?

---

### Post by xigen on 2014-09-03
I ... via trial and error .. learned to select #14  IP addrss (*of printer)

for me:  192.168.2.138

When I selected choice #14 and plugged in my printer's IP everything worked.

---

