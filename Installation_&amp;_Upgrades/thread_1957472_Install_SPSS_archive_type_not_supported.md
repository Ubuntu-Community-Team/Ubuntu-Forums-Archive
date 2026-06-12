---
title: "Install SPSS: archive type not supported"
date: 2012-04-12
forum: Installation &amp; Upgrades
---

### Post by Maxence on 2012-04-12
Hi,
After downloading from the IBM webpage the SPSS Statistics20 for Linux data, I tried to install it but I got the message: Archive type not supported
The downloaded file is a .bin.gz file 
Any help is very welcomed! Thanks!
max

---

### Post by Maxence on 2012-04-23
Hi found my way through it at now it works perfectly fine. Here is how I proceeded:

1. Download the software from [http://www14.software.ibm.com/download/data/web/en_US/trialprograms/W110742E06714B29.html](http://www14.software.ibm.com/download/data/web/en_US/trialprograms/W110742E06714B29.html)

- choose the Linux version, click on Continue and Proceed without an IBM ID
- enter your personal information and the download will start

2. Extract the CI3HXML.bin.gz file which is the one you downloaded

- Once you have your CI3HXML.bin file, right click on it, Properties --> Permissions and Allow executing file as a program
- Go to the terminal and type: sudo ./CI3HXML.bin

3. Install SPSS 20

- Follow the installation guide
- Register the programm with the licence key (maybe optional for a trial version)

4- Run SPSS

- Go to the terminal and type: /opt/IBM/SPSS/Statistics/19/bin/stats

--> the programm will run by itself. Every time you will have to start the programm like this. Don't close the terminal, if not you will end SPSS. 
I didn't find a way to do it differently
:D

---

