---
title: "Opening Open Office 3"
date: 2013-04-06
forum: Installation &amp; Upgrades
---

### Post by SpikeLS6 on 2013-04-06
I transferred my Desktop 12.04 from Libre Office to Open Office successfully (Libre Calc corrupted several of my spreadsheets).

Moving to the laptop with 12.04 I removed Libre Office with:
   sudo apt-get remove --purge libreoffice-core

Then I downloaded and installed Apache Open Office 3 with:
   sudo add-apt-repository ppa:upubuntu-com/office
   sudo apt-get update
   sudo apt-get install open office

It gave an aptdaemon error, so I input the suggested correction of:
   sudo dpkg --configure -a

Now I can go to Dash Home and find a folder with OpenOffice.org 3. What file can be used in that folder to start the application? Then I will move the icon to the launch bar for future use.

Spike

---

### Post by Hagar Delest on 2013-04-08
Personally, I install the deb package from the Apache site, then install with dpkg. See: [[Ubuntu] Installing OOo on Debian and Co.](http://forum.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

The scripts are in the /program folder.

But better make custom .desktop files in your local folders that points to the correct scripts.

---

### Post by SpikeLS6 on 2013-04-14
Tried the .deb installations as you suggested and the See: [[Ubuntu] Installing OOo on Debian and Co.]("http://forum.openoffice.org/en/forum/viewtopic.php?f=16&t=68"). Always got an error or it could not find a file it wanted, or it did not have access to what it wanted. I'll keep working at it.

Spike

---

### Post by Hagar Delest on 2013-04-14
What is the error message exactly?

---

### Post by SpikeLS6 on 2013-04-15
Errors from the dpkg commands:

mike@mike-HP-Pavilion-dv9700-Notebook-PC:~$ sudo dpkg -i whatever .deb
[sudo] password for mike: 
dpkg: error processing whatever (--install):
 cannot access archive: No such file or directory
dpkg: error processing .deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 whatever
 .deb
mike@mike-HP-Pavilion-dv9700-Notebook-PC:~$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
mike@mike-HP-Pavilion-dv9700-Notebook-PC:~$ cd desktop-integration
bash: cd: desktop-integration: No such file or directory
mike@mike-HP-Pavilion-dv9700-Notebook-PC:~$ sudo dpkg -i *deb
dpkg: error processing *deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *deb
mike@mike-HP-Pavilion-dv9700-Notebook-PC:~$ 


Does this help?

Spike

---

### Post by Hagar Delest on 2013-04-15
I think that you're not in the correct folder. Type pwd and make sure that you're in the folder where are the .debs. If you type ls then you should see all of them.
Use the cd command to navigate to the correct folder (just follow the instructions in the tutorial).

---

### Post by SpikeLS6 on 2013-04-16
Tried to change the directory with this:

mike@mike-HP-Pavilion-dv9700-Notebook-PC:~$ cd /home/downloads/en-US/DEBS
bash: cd: /home/downloads/en-US/DEBS: No such file or directory
mike@mike-HP-Pavilion-dv9700-Notebook-PC:~$ cd: /home/downloads/en-US/DEBS
No command 'cd:' found, did you mean:
 Command 'cde' from package 'cde' (universe)
 Command 'cdb' from package 'tinycdb' (main)
 Command 'cdo' from package 'cdo' (universe)
 Command 'cdi' from package 'cdo' (universe)
 Command 'cdv' from package 'codeville' (universe)
 Command 'cdw' from package 'cdw' (universe)
 Command 'cd5' from package 'cd5' (universe)
 Command 'cdp' from package 'irpas' (multiverse)
cd:: command not found
mike@mike-HP-Pavilion-dv9700-Notebook-PC:~$ cd home/downloads/en-US/DEBS
bash: cd: home/downloads/en-US/DEBS: No such file or directory
mike@mike-HP-Pavilion-dv9700-Notebook-PC:~$ ^C
mike@mike-HP-Pavilion-dv9700-Notebook-PC:~$ ^C
mike@mike-HP-Pavilion-dv9700-Notebook-PC:~$ 

Then reread your reply and used the "pwd" command:

mike@mike-HP-Pavilion-dv9700-Notebook-PC:~$ pwd
/home/mike
mike@mike-HP-Pavilion-dv9700-Notebook-PC:~$ cd /home/mike/downloads/en-US/DEBS
bash: cd: /home/mike/downloads/en-US/DEBS: No such file or directory
mike@mike-HP-Pavilion-dv9700-Notebook-PC:~$ ls
Desktop    examples.desktop  nvidia-bug-report.log.gz  Templates
Documents  fontconfig        Pictures                  Ubuntu One
Downloads  Music             Public                    Videos
mike@mike-HP-Pavilion-dv9700-Notebook-PC:~$ 

 I am missing something.

Spike

---

### Post by Hagar Delest on 2013-04-16
You need to know where you've extracted the debs exactly.
And then cd to the directories mentioned above.

---

### Post by SpikeLS6 on 2013-04-17
I can see my DEBS Folder at Home/Mike/Downloads/en-US/DEBS. I use the CD command to change directories, but is always give me an error saying that the no such file or directory exists. Using GDebi, when I load the DEBS Folder into GDebi, it takes it but installing the folder always tells me that the file is locked or I do not have authorization to open it.

I have run out of time before the weekend, so my next plan is to purge anything related to Open Office on the hard drive, then begin again with the second option explained in the artilce titled "How do I install OpenOffice.org instead of LibreOffice?"

Thank you for your help; sorry I have not done any better.

Spike

---

### Post by Hagar Delest on 2013-04-17
Perhaps you've extracted using root (sudo). You should extract the file as a standard user.

---

### Post by amanchesterman on 2013-04-17
I'm fairly new to Linux so maybe this comment will be no help at all. But like you, Spike, I've had problems using the 'cd' command and I found through experience that it was due to being careless about capitalisation when typing the names of directories. In your post #9 you say your DEBS folder is at Home/Mike/Downloads/en-US/, but in your post #7 you tried to cd to home/mike/downloads/en-US -- which is quite different. Which is right? (In my case it would be home/john/Downloads etc., which is different again!)
John

---

### Post by Hagar Delest on 2013-04-17
Good catch. When you cd, use the Tab key: start typing the first letters of the path and hit Tab to auto-complete. If nothing comes up, it means that the name of the folder is wrong.

---

### Post by SpikeLS6 on 2013-04-18
To restart with a clean slate, I did a: sudo apt-get remove --purge openoffice*.

I went to the "How do I install OpenOffice.org instead of LibreOffice?" article recommended. Then I followed the rest of Option 2. I downloaded a fresh .tar.gz from the Apache Open Office web site, and put it into it's own folder. In that folder I used Archive Manager to extract the downloaded file. This time I was able to drag the DEB folder into Terminal and it installed properly. Then I went back to Option 1 and the same with the Desktop Integration folder within the DEBS folder. It installed correctly.

Going to the Dash Panel, I found all the Icons for Open Office 3.4, tried them all and all the applications come up properly.

Thank all of you for your help; without it I would never have been able to get things straight with Open Office. I got tired of Office Libre eating my spreadsheets, even if it is supposed to be an approved clone. The formattings are better, for me, in Open Office, too. 

Now I need to locate the [SOLVED] symbol somewhere. 

Thanks again!

Spike

---

### Post by SpikeLS6 on 2013-04-18
I wish I could find the [SOLVED] indicator for the Title; it is not where I used to find it in the Thread Tools.

I purged everything Open Office, including the downloads that were corrupted, locked, or had other problems with:
    sudo apt-get remove --purge openoffice

Then I began with a fresh download from Apache Open Office as per Option 2 of the recommended article "How do I install OpenOffice.org instread of LibreOffice".

After completing Option 2 5), I went back to Option 1, last paragraph and command line, put the "desktop-integration" folder into Terminal and commanded:
    sudo dpkg -i *.deb.

Next I checked Dash Home and found all the Open Office Icons. I brought up each one and each came up without a problem. I think my issues of replacing Office Libre with Open Office are Solved. Any one know where the [SOLVED] prefix has been moved?

Thank you everyone for your help. Without it I would not have figured this out.

Spike

---

### Post by Hagar Delest on 2013-04-18
In this forum, you've to add the [Solved] tag to the title of the first post in the thread.

---

