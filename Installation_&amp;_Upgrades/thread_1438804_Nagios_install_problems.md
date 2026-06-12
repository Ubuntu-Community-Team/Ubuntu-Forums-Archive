---
title: "Nagios install problems"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by kel_gb on 2010-03-25
Hi All

I'm trying to install nagios on Ubuntu 9.10 (desktop) but keep getting the same error when I enter the 'make install-webconf' command

make: *** No rule to make target `install-webconf'.  Stop.

I've followed the quick install guide from the nagios web site and even tried searching around the web for a solution but I can't seem to find one. All other commands prior to this have worked fine.

Has anyone else come across this problem and found a solution?

Nb - i'm not a complete linux newbie but am not exactly advanced so clear instructions would be awesome and I'd appreciate the help.

Thanks
Kel

---

### Post by gordintoronto on 2010-03-25
The format of the command is incorrect.  I suspect there should be a space before the dash, but that is just a guess.

It would have been helpful to provide a link to the "quick install guide," which I have not been able to find on the Nagios web site.  Did you cut and paste the command from the guide?

---

### Post by kel_gb on 2010-03-26
Hi

Sorry the link is: [http://nagios.sourceforge.net/docs/3_0/quickstart.html](http://nagios.sourceforge.net/docs/3_0/quickstart.html)

Looks like the instructions didn't include a space before the -webconf

Thanks gord, Much appreciated - it's always the simplest things isn't it :) 

Kel

---

### Post by deznuts05 on 2010-04-05
Not sure if this is a related problem however in parting of creating my nagios software I tried to assign the machine a static ip.

Once I was able to do that I lost the ablity to access the internet. What I've done to resolved that was to remove the network manager and manually edit the interfaces file.

I now have access to the internet however I've lost the ability to access [http://localhost/nagios](http://localhost/nagios)

anyone else have this problem?

---

### Post by Notandi on 2010-05-07
The URL to Nagios is localhost/nagios3

Default user is nagiosadmin but there is a JRock YouTube video for that. 

I gave up on Ubuntu for Nagios. It puts everything in the wrong directory. Presently trying SUSE but its not much easier.

---

### Post by Lord_Dicranius on 2010-05-09
Yeah, I tried installing Nagios via the repositories too, but didn't like that everything was in the /etc directory.  Especially considering all of the guides you read says it's installed in /usr/local.  I just followed the Ubuntu quickstart guide over on the Nagios site.  Even though it says the guide was written using 6.10, it still worked for me on 10.04!

---

