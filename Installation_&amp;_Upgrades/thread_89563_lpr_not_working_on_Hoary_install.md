---
title: "lpr not working on Hoary install"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by benblout on 2005-11-12
Hi all,

I have a Hoary install which I completed about four months ago.  The lpr 
command has never worked for me.  I am not planning to install Breezy (5.10) on
this machine, so I would love to get this fixed.

I used the command

sudo gnome-cups-manager

to install my printer (HP LaserJet IIIp with postscript) with no problems, including
setting it to be my default printer.  Printing a test page from gnome-cups-manager
works great.

However, trying to print a postscript command from the command line fails,
as does the lpq command:

blout@chipmunk:~ $ lpr mozilla.ps
lpr: error - scheduler not responding!
blout@chipmunk:~ $ lpq
lpq: error - no default destination available.

For the last few months, I have been using the workaround of sending
files directly to the printer:

cat mozilla.ps > /dev/lp0

which works just fine.

I played with lpstat -a and lpstat -d:
blout@chipmunk:~ $ lpstat -d
no system default destination
blout@chipmunk:~ $ lpstat -a
LaserJet-3P-w/PS accepting requests since Jan 01 00:00


I saw there was a printer, so I tried specifying it specifically:

blout@chipmunk:~ $  lpr -P LaserJet-3P-w/PS mozilla.ps
lpr: error - unable to print file: client-error-not-found
blout@chipmunk:~ $ lpq -P LaserJet-3P-w/PS
lpq: Unknown destination "LaserJet-3P-w/PS"!

Any suggestions would be great,

Ben

---

### Post by benblout on 2005-11-13
[QUOTE=benblout]
I have a Hoary install which I completed about four months ago.  The lpr 
command has never worked for me.  I am not planning to install Breezy (5.10) on
this machine, so I would love to get this fixed.
<snip>
However, trying to print a postscript command from the command line fails,
as does the lpq command:

blout@chipmunk:~ $ lpr mozilla.ps
lpr: error - scheduler not responding!
blout@chipmunk:~ $ lpq
lpq: error - no default destination available.
<snip>
I played with lpstat -a and lpstat -d:
blout@chipmunk:~ $ lpstat -d
no system default destination
blout@chipmunk:~ $ lpstat -a
LaserJet-3P-w/PS accepting requests since Jan 01 00:00
[/QUOTE]

I think I have some of the problem solved.  I tried to set the default printer:

blout@chipmunk:~ $ lpadmin -d LaserJet-3P-w/PS
lpadmin: Printer name can only contain printable characters!

I tried to change the name of the printer in gnome-cups-manager; that did not
work.  So I edited the /etc/cups/printers.conf file directly, changing this:

<DefaultPrinter LaserJet-3P-w/PS>
Info LaserJet-3P-w/PS

to this:

<DefaultPrinter ben3p>
Info 3p

I also copied the file  /etc/cups/ppd/LaserJet-3P-w_PS.ppd
to the file /etc/cups/ppd/ben3p.  I restarted cups - and it worked!

blout@chipmunk:~ $ lpstat -a
ben3p accepting requests since Jan 01 00:00
blout@chipmunk:~ $ lpstat -d
system default destination: ben3p
blout@chipmunk:~ $ lpr mozilla.ps
blout@chipmunk:~ $ lpq
ben3p is ready and printing
Rank    Owner   Job     File(s)                         Total Size
active  blout   1       mozilla.ps                      171008 bytes

So, this seems like a bug to me.  I believe that the slash is what is giving
things fits.  I haven't bug-reported in Ubuntu before - do I file the bug
here, and it get forwarded upstream, as it does in Debian?

Or is this still a case of user error?

-Ben

---

