---
title: "unable to download printer drive for Epson XP-640"
date: 2017-12-12
forum: Installation &amp; Upgrades
---

### Post by davidhopton on 2017-12-12
I use Ubuntu 16.01 and have trouble downloading from Epsom download centre. Centre requests you first download current version of lsb 3.2 which I have done with no success. This is a somewhat usual problem in the forum. I note one solution that I would like to try but the instructions end with "deb" (quotes not included). My understanding this stands for Debain which is another free-source system (linux?)   My QUESTION is is it safe for me to try? ----I am only semi literate with computers,  I have also looked at other free-source sites but the XP-640 is not listed.

---

### Post by DuckHook on 2017-12-12
Ubuntu is based on Debian. Most of Ubuntu's native packages end with .deb.

This does not mean that every .deb is "safe". Apart from the usual warnings about unknown downloads from unsafe sites, there is also the question of compatibility: a newer package from outside the repositories will sometimes break the intricately linked dependencies of your OS.

However, in this case, I would think it is safe to try. *lsb* stand for (L)inux (S)tandard (B)ase, and is a set of core functions that third-party developers can use to build apps/drivers on. *lsb* is available in the repos, but that version is probably too old to run your driver, hence, Epson's requirement to download *lsb 3.2*. A standard package available in the repos coupled with Epsom being a reputable company probably means that the download won't have malware lurking inside. Moreover, one hopes that it has been tested and is "safe to run" in that respect too. The usual caveats apply: make backups before doing anything to your system.

---

### Post by davidhopton on 2017-12-13
DH- thank you for your reply. I tried it and I still cannot download the driver. The Linux 
Foundation has a long list of Epson drivers ( for downloading) but not for the XP-640
Previously, I did not express myself correctly. I did download lsb3.2 successfully but was unable to to successfully download any of the 5 drivers Epson recommended. I am at a total loss --lI have checked many other threads and atried many of the recommendations with no success

---

### Post by ian-weisser on 2017-12-13
You should not have needed to download lsb 3.2
ALL currently-supported releases of Ubuntu already exceed 3.2 by quite a bit. 3.2 is *very* old.

All you should need to do is:
1) Download the printer driver deb file from the Epson website to your Desktop

2) Open a Terminal

3) Install lsb (newer than 3.2)
At the terminal prompt '$' do:
```
sudo apt install lsb
```
The system will prompt you for a password. THE SCREEN WILL NOT SHOW that you are typing your password. This is normal. Keep typing your password.
There should be a few cryptic lines, then a return to a '$' prompt.

READ those cryptic lines. Look for the words 'error' or 'warning'. If there are any errors or warning, stop. Return here, and copy-and-paste the complete output into your reply. Not just one or two lines, but the whole thing from $ (start) to $ (finish).

4) Install the Epson Print Driver deb that you saved to the desktop
```
sudo apt install ~/Desktop/<exact_name_of_the_file>.deb
```

Again, look for errors or warnings.

5) Test your printer.

---

### Post by davidhopton on 2017-12-13
per your instructions, I did items 1),2)& 3 and received no error warnings, etc. I then went to 4) and received following "missing destination file oper and after" the exact name of the file. I am certain that I used the exact name of he file.
I hope this is clear enough and I really appreciate your having taken the time to help me. thank you

---

### Post by DuckHook on 2017-12-13
> **davidhopton said:**
> …I tried it and I still cannot download the driver…
> **davidhopton said:**
> …per your instructions, I did items 1),2)& 3 and received no error warnings, etc…
> **davidhopton said:**
> …Previously, I did not express myself correctly. I did download lsb3.2 successfully but was unable to to successfully download any of the 5 drivers Epson recommended…
:confused:
I am confused. So you *can* download the driver but you cannot *install* it? If you can't download, how did you carry out step 1? Is your browser refusing to download from Epson's site?

I would suggest that from now on, rather than simply describing what you think is the problem, that you post the actual input and output within [noparse]```
 and 
```[/noparse] tags the way Ian and I do. That way, we will see the actual error messages that constitute the really useful info to us.

Therefore, try #4 from Ian's instructions again, but post the verbatim command you are using and the actual verbatim error message. You can use your mouse to highlight the code and right click to copy and paste.
> The Linux Foundation has a long list of Epson drivers ( for downloading) but not for the XP-640
The Linux Foundation's list of compatible drivers is not up-to-date, especially for newer models. How can it be? New printer models are released practically every day. The important info is from the Epson site. They would have Linux drivers (or not) and installation instructions for each new model that they make. Visiting the Epson site yields the following:

The following are your downloads: [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

Was this the site you tried downloading from? If not, then download these drivers and try installing again.

---

### Post by ian-weisser on 2017-12-13
> **davidhopton said:**
> I then went to 4) and received following "missing destination file oper and after" the exact name of the file. I am certain that I used the exact name of he file.

Copy and paste the terminal session here, showing exactly what you input, and exactly what the system output.
It's usually something trivial, like you used the wrong case or the wrong destination or mistook a letter for a number (0/O/o, 1/l) or missed a dash or a period somewhere.

---

### Post by davidhopton on 2017-12-14
I copied it from the terminal and could not paste it in my quick reply so I copied it to a document in my computer. For some reason, when I try and copy and paste from my computer to this message it will not take. I appreciate your suggestion that I made an incorrect entry somewhere --Idon't think  did but I will re-enter and then advise you of the results. 
In response to the previous reply "I am confused" when I download the epson driver, it appears under my downloads but it will not open. I will report back           OBVIOUSLY I was wrong about copy and paste

---

### Post by davidhopton on 2017-12-14
Just retried-- here is the message 
```
david@david-Inspiron-560:~$ sudo apt install-/desktop/epson-inkjet-printer-escpr_1.6.17-1lsb_i386.deb
[sudo] password for david: 
E: Invalid operation install-/desktop/epson-inkjet-printer-escpr_1.6.17-1lsb_i386.deb
david@david-Inspiron-560:~$
```

---

### Post by ian-weisser on 2017-12-14
You made THREE typos. Read the command very carefully and try again.
Pay careful attention to spaces, dash-vs-tilde (-/~), and typeCASE (lower vs upper)

Hint: 'desktop' is a different location than 'Desktop'. Case matters.

---

### Post by davidhopton on 2017-12-14
I believe I did it correctly 

```
david@david-Inspiron-560:~$ sudo apt install ~/Desktop/epson-inkjet-printer-escpr_1.6.17-1lsb3.2_i386.deb
[sudo] password for david: 
Reading package lists... Done
E: Unsupported file /home/david/Desktop/epson-inkjet-printer-escpr_1.6.17-1lsb3.2_i386.deb given on commandline
david@david-Inspiron-560:~$
```

---

### Post by davidhopton on 2017-12-14
Another try

```
avid@david-Inspiron-560:~$ sudo apt install~/Desktop/epson-inkjet-printer-escpr_1.6.17-1lsb3.2_i386dep
[sudo] password for david: 
E: Invalid operation install~/Desktop/epson-inkjet-printer-escpr_1.6.17-1lsb3.2_i386dep
david@david-Inspiron-560:
```

---

### Post by oldos2er on 2017-12-14
You're missing a space between "sudo apt install" and  "~/Desktop/epson-inkjet-printer-escpr_1.6.17-1lsb3.2_i386dep"

And it's "deb," not "dep." Tab completion is your friend.

---

### Post by DuckHook on 2017-12-14
You are likely running a 64-bit Ubuntu OS. However, you have downloaded the 32-bit driver. This, combined with the typos, is likely what's tripping you up.

[LIST=1]
[*]The following is the download page for scanner: [http://support.epson.net/linux/en/imagescanv3.php?version=1.3.23](http://support.epson.net/linux/en/imagescanv3.php?version=1.3.23)
[*]
[*]You must pick the one that says: "Ubuntu 16.04(LTS)"&#8594;"64bit(amd64)"
[*]
[*]For printer: [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=66609&DSCCHK=acc94f2a6fa073d24f9cdad2fb125f28ce00eb97](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=66609&DSCCHK=acc94f2a6fa073d24f9cdad2fb125f28ce00eb97)
[*]
[*]Pick the one that says: "epson-inkjet-printer-escpr_1.6.17-1lsb3.2_amd64.deb"
[*]
[*]For printer utility: [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=67510&DSCCHK=91eb5ed19b89a820f2b2f68849ea90e4a8a5b670](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=67510&DSCCHK=91eb5ed19b89a820f2b2f68849ea90e4a8a5b670)
[*]
[*]Pick the one that says: "epson-printer-utility_1.0.2-1lsb3.2_amd64.deb"
[/LIST]
Ignore the "amd" part in these drivers. They don't mean they are only for AMD CPUs; they apply to Intel CPUs as well. What they really mean is 64-bit. This is an old (and silly) Linux convention that trips a lot of new users up and you can't blame yourself for downloading the wrong drivers.

To avoid further typos, best to copy and paste these above lines into your terminal. Don't copy the quote marks ("), though they shouldn't do any harm either. Then, before pressing the enter key, check carefully to make sure that all spelling, capitalizations and typing are accurate.

I know it's frustrating to butt heads up against simultaneously arcane and persnickety Linux commands, but you only have to get it right once.

---

### Post by davidhopton on 2017-12-15
Well, I finally got the printer to work. I really appreciate the patience and time extended by all.

---

### Post by DuckHook on 2017-12-15
Good to know that you're up and running.

If you consider this matter resolved, please mark thread "solved" using thread tools at the top of this thread, so that others can benefit from your solution.

As a postscript, it was only possible for me to effectively help once you posted actual inputs and outputs. Prior to that, we were just spinning our wheels. In future, when requesting help, it is less frustrating and more efficient to all if you post that info from the outset.

Good Luck and Happy Ubuntu-ing!

---

### Post by Darth4212 on 2017-12-15
I went through the official Epson site and came to this website[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule) where you can search for drivers I was able to find 3 drivers for the Epson XP-640 printer

---

