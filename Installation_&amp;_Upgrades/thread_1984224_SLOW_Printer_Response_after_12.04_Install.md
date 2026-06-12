---
title: "SLOW Printer Response after 12.04 Install"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by WilhelmGGW on 2012-05-21
Last week I did a clean, fresh, full install of 12.04 on a Dell destop, where I previously ran various iterations and versions of Ubuntu. Everything fine *except* I can't get my network printer to respond as it should. I have tried every imaginable setup to make it work. 

I've done prior installs on three other Ubuntu machines--usually difficult, put in the end successful.. and printing fast as they should be.

But on this install, the best I can get is a setup that sometimes prints in a minute or more, sometimes never.  Any suggestions?  Thanks in advance.

I'm wired in to a home network with a Brother HL-5370DW printer.

---

### Post by kurt18947 on 2012-05-21
Have you tried Brother's installer?  It's a bash script that seems to work pretty well.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

You *may* have to edit the device URI after running this script depending on your network.

---

### Post by WilhelmGGW on 2012-05-21
> **kurt18947 said:**
> Have you tried Brother's installer?  It's a bash script that seems to work pretty well.

Yes. I tried it before, and just tried it again. I've tried everything I could find on the Brother support site. Everything works equally bad.

You know.. I think I have a more systemic problem with this.  If I open the System Monitor - Resources - CPU History, when I click to print a document, the CPU of one core spikes to 1000% and stays there for a long time.  Then it drops down, the Network History revs up on the Sending side, and the status light on the printer begins blinking.  That goes on for a while, then finally the document will (usually) print.

Once a print job finally clears, everything returns to normal on the System Resource Monitor.  Other than this issue with printing, nothing else on the computer seems slow, choked, throtled, or otherwise starved for available cycles.

---

### Post by WilhelmGGW on 2012-05-21
BUMP  Any other ideas, anyone?

---

### Post by iainteunon on 2012-05-23
I have a similar problem. Printing can take anything up to 8 minutes, especially if the page contains a picture. My printer is a HP Laser Jet 400N connected to my HP Compaq by the parallel port.

---

### Post by WilhelmGGW on 2012-05-23
> **WilhelmGGW said:**
> I think I have a more systemic problem with this.  If I open the System Monitor - Resources - CPU History, when I click to print a document, the CPU of one core spikes to 1000% and stays there for a long time.  Then it drops down, the Network History revs up on the Sending side, and the status light on the printer begins blinking.  That goes on for a while, then finally the document will (usually) print.

Also.. When the print job is hung up -- hogging resources and "processing" -- I've found that it sometimes suddenly releases from its hung state and prints immediately *exactly when I execute some other input command to the system*.  When that's happened, I've been so wonderfully ecstatic that I've not noted exactly what I did that got things going.  But it's like *yes!* there is *something* that releases whatever processing bottleneck that there is and lets printing proceed as it should.

---

### Post by Bruce.314 on 2012-05-27
Ubuntu 12.04 64bit.
Identical problem.
Brother HL-5370 DW network printer using port 9100.
Printing page from LibreOffice Writer takes only a few seconds.
Printing 1st page from this forum using Firefox takes 5 minutes!
All 4 pages take almost a half-hour.
I'm wondering if the driver is trying to pixilate my document at 1200 dpi?
(it's set at 600. Trying 300 has no effect.)
Both of my CPU cores are running at about 20 percent.
My 2g memory is at about 50 percent.
My network output (to the printer) is 20-40 Kbytes/sec.
Hope you get a new driver soon.
Bruce

---

### Post by WilhelmGGW on 2012-05-27
We may need a new driver, Bruce. I'm pretty sure I've tried every indicated driver out there -- from Ubuntu and Brother alike -- and nothing improved the situation.

What's puzzled me is that the Ubuntu driver has worked well on every prior Ubuntu version I've run. Just not on this clean install of 12.04.

---

### Post by ssivil on 2012-06-07
I have the exact problem with my HL-5370 DW connected thru socket://192.168.1.253 to my wireless router.

Because printing is too important, I moved to Fedora 17.  Printing now begins in less than a minute vs 20 (same document).

---

### Post by WilhelmGGW on 2012-06-08
Problem has solved itself with some regular system update. Thanks for listening, Ubuntu.

---

### Post by DDDa on 2012-11-12
Yes, this is old. But one additional note since I have this very same printer and had the same problem:

I was trying the PPD file supplied (just that). While it installed and printed well, I was suffering from this *horrible* delay before printing. It would spool and spool and wait... horrible indeed.

Then I tried others, [the LPR and the cupswrapper driver]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-5370DW").

Downloaded the two deb files and followed the [instructions]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html"). Very easy, no way to get it wrong.

It installed a new USB printer, so I modified it for networking printing. Per the instructions, I modified the location to:

```
lpd://<printer-ip>/binary_p1
```

It's set as a "LPD/LPR Host or Printer", and the driver is the one supplied by the files. It's called exactly "Brother HL5370DW for CUPS (en)". There are other HL-5370DW drivers listed in the CUPS admin web page (!!!), but just in case I selected these, which were the ones installed by the downloaded files.

If you're using a 64 bits system (Xubuntu 12.10 x64 here), the instructions also tell you to install the ia32-libs package.

And now the slow printing problem solved. It was especially problematic with PDF files with graphics, for what I've seen.

Fast printing everyone! :)

---

