---
title: "how to launch fslurp"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by Halcyon31415 on 2010-04-04
So i think this is going to be a bone head question but, I downloaded the program fslurp from source forge [http://sourceforge.net/projects/fslurp/]("http://sourceforge.net/projects/fslurp/") in case you would like to check it out. So the file downloads into a .tgz looking online i downloaded Alien to convert it to a .deb file. (feeling really good about my self at that point btw :p) so the program then says it installs but i can't for the life of me figure out how to run the program now that it is installed. I did a file search for fslurp but all i get are the original .tgz and the .deb files and nothing else. Well hopefully there is a sweet explanation for this, if anyone can let me know i would appreciate it. 

Thank you in advance!

---

### Post by Halcyon31415 on 2010-04-06
I got in contact with the author of the program. This was his response to my question.

There are two issues with being able to run the program.
 The first is whether or not the binary shipped is compatible with
your installation.  If it isn't you will need to rebuild it.
Rebuilding it can be done with the following steps:

$ cd /wherever/you/put/it/fslurp-0.5
$ make clobber
$ make

And then to run it, from the same directory:

$ ./fslurp -h

This will display the following help message:

Usage: ./fslurp [-b baud][-d delimiter][-H][-h][-p device][-r report][-v]
       -b baud Set the baud rate.  Supported rates are:
                       2400, 4800, 9600, and 19200. Defaults to 9600.
       -d delimter     Set delimiter for CSV-style output. The
                       default is no delimiter, human-readable.
       -H              Display the delimited output header for the
                       current reporting mode.  The -d option must
                       also be set.
       -h              Display this help message.
       -p device       Set the serial port device. Defaults to /dev/ttyS0.
       -r report       Set report type. Supported types are:
                       now, day, total, and all  Defaults to now.
       -v              Enable verbose, debugging output.

Return codes:
       0       Success.
       1       Communications failure.
       2       No active inverter found.
       3       Usage error.
       4       Fronius protocol error.

At this point, you are running the program, and you will need a serial
cable from your Linux box to the Interface Easy Card in your Fronius
inverter.

---

### Post by two9er on 2010-05-19
Running a script from cron to log my fronius output:

```
#crontab -e
* * * * * /root/fronius.sh
```and the contents of fronius.sh:

```
sheevaplug-debian:~# cat fronius.sh
#!/bin/bash
TZ='America/Denver'; export TZ
/root/fslurp-0.6/fslurp -r all -d , -p /dev/ttyUSB2 >> /media/sda1/fronius.log
```This aggregates to fronius.log which can then be parsed as you see fit.

Sample:
Wed May 19 08:52:01 2010,Wed May 19 08:52:01 2010,2,1.2.2,0x1,FRONIUS IG 3000 1-phase inverter,678,2.79,243,59.97,3.91,188,1,2364,245,242,192,1.48,8338,2872,250,0,236,6073.00

I had fslurp running from my 'buntu desktop, but recently compiled it on a guruplug server (which BTW can run ubuntu also):
 
[http://www.globalscaletechnologies.com/p-32-guruplug-server-plus.aspx](http://www.globalscaletechnologies.com/p-32-guruplug-server-plus.aspx)

FWIW,

Jim

---

