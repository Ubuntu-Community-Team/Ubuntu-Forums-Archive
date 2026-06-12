---
title: "Hear to help and learn"
date: 2010-03-19
forum: Louisiana Team - US
---

### Post by ad5xj on 2010-03-19
Hi Ken here. I am located in Houma, LA An avid Ubuntu 9.10 user and ham radio operator. I am also WebMaster for the Louisiana ARRL Section Web site designed and maintained from Ubuntu Linux.

I have been a programmer for 25+ years and now program in C++ using Nokia Qt SDK for Open Source. I have a current project on sourceforge.net called DXCentral. It is a desktop widget for Linux and Windows.

I am also an ARRL Technical Specialist in Louisiana actively promoting the use of Linux for ham radio operators.

---

### Post by rosserver on 2010-03-30
Hi, Ken;
I'm Ross (in Slidell) aka KB5FJR.

---

### Post by ad5xj on 2010-03-31
Hi Ross

I am finding more and more hams on Ubuntu and in Qt forums.

Not sure if you are ARES but I am DEC for region 3 and I do the ARES EchoLink forum on *LA_ARES* conference. I am also the Section WebMaster and Technical Spec.

I have a Qt project on sourceforge.net called DXCentral (not affiliated with [www.dxcentral.com](www.dxcentral.com)).

Hope to hear you on EchoLink or on the air.

---

### Post by kinkajou45 on 2010-10-06
Hi, Ken. QTH Houston.

Hope I'm not OT, but can one of you please give me the command line script to create a panel launcher for Hamsphere-which opens with OpenJDK Java 6 Runtime . 

I'm learning a lot from Hamsphere.  I don't have my technician license yet, but am up to 97% average on my practice tests from various sites. I don't have a modern rig and never had the chance to use one, so Hamsphere was the answer to a prayer.  It puts a face on the unknown, so to speak.

I do however, have a couple of stupendous antique radios via my spouse's garage and attic.  One is a c1932 kit with home brew telegraph key, the other is Hallicrafter's Model S04-B. In the process of learning how to restore those bad boys right now. So I'm not doing too bad for a total  noob.

If y'all can help, thanks in advance.

---

### Post by ad5xj on 2010-10-20
Ok here is what you do.

Obviously, you must download the app using a callsign (or in your case no callsign). The signup script will assign you a call to use in the app.

After downloading, put the .jar script in your /bin directory in a folder of your choice. DO NOT UNZIP OR EXPAND! I created a folder called Hamsphere. Move the .jar file to this folder. Use the file manager to examine the properties. Change the execute property to a check for all.

Now you can create a launcher on your desktop that starts the app in a terminal. The command line should read - 
java -jar [your folder path]/hamsphere_2.0.19_for_linux_and_mac.jar

This assumes you have jre installed on your distro.

When the app starts you can put your assigned call in the callsign box with the password you gave to register. It should be working after you click the login button.

---

