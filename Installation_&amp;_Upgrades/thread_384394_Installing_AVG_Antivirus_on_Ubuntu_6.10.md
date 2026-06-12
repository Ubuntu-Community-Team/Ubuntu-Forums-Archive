---
title: "Installing AVG Antivirus on Ubuntu 6.10"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by ctsit on 2007-03-14
I'm completely new to Linux and I started off with Ubintus 6.10 Version (I think a wise chose since its pretty straight forward) but I have a problem installing AVG Anti virus Version avg71flm-r30-a0791.i386.rpm.  When I double click the installation package I get a message  "could not open file avg71flm-r30-a0791.i386.rpm Archive type not supported"

Any ideas, please people help a newbie

Chris

---

### Post by omockler on 2007-03-14
Ubuntu is built on the debian distribution and usually uses packages that end in .deb instead of .rpm. rpm is the Red Hat distros package manager.  You should try to find a package that ends in .deb or maybe .tar.gz.   Hope that helps!


Here is a link to the .deb version of "AVG Anti-Virus Professional Edition 7.5":
[http://www.grisoft.cz/filedir/inst/lnx_alx_stf__7_5-0045.dir/avg75lms-r45-a0970.i386.deb]("http://www.grisoft.cz/filedir/inst/lnx_alx_stf__7_5-0045.dir/avg75lms-r45-a0970.i386.deb")

---

### Post by stchman on 2007-03-14
> **ctsit said:**
> I'm completely new to Linux and I started off with Ubintus 6.10 Version (I think a wise chose since its pretty straight forward) but I have a problem installing AVG Anti virus Version avg71flm-r30-a0791.i386.rpm.  When I double click the installation package I get a message  "could not open file avg71flm-r30-a0791.i386.rpm Archive type not supported"

Any ideas, please people help a newbie

Chris

.rpm are red hat distributions.  You need to convert that .rpm to a .deb.  You can do that with alien.  To install alien type the following:

sudo apt-get install alien

After alien iistalls you will envoke this command:

sudo alien -k avg71flm-r30-a0791.i386.rpm

You will thne get a corresponding .deb file.  This you can double-click on and install.

Enjoy

---

### Post by ctsit on 2007-03-14
thanks both I've already installed AVG but I don't see the program files or any screen to upgrade or customize the antivirus

any ideas

---

### Post by Monster_user on 2007-03-18
Assuming your using Ubuntu, try this.

Actions -> Run -> gksu avggui

Enter your Root password, and then it should load AVG. To use AVG, just create a "shortcut"/launcher to it, using the 'gksu avggui' command.

---

### Post by the.phantom on 2007-03-19
just a quick note

avg has updated to 7.5  and 71. will not be supported

BUT they have released it in a deb package ( the good news)
but the program has some bugs ( the bad news)

i'm monitoring their linux support forum for the free version and hopefully the bugs will be fixed soon

---

### Post by swejuggalo on 2007-03-20
Anyone has been able to install avg free 7.5 on 6.10 yet? Complains on a lot of thing all the time during install... Not being able to kill services, or missing files, AND complains if files exist... A lot of problems in other words... Must I clean the system from avg-free 7.1 manually and stuff?

---

