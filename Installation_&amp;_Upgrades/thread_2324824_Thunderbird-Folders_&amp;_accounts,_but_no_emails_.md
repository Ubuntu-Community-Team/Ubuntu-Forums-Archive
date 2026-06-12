---
title: "Thunderbird-Folders &amp; accounts, but no emails after upgrade"
date: 2016-05-16
forum: Installation &amp; Upgrades
---

### Post by SoFl W on 2016-05-16
I upgraded from 12.4 to 16.4 mate.  Thunderbird works fine with 12.4.  I followed the instructions found in other forums and on the Mozzilla website about how to transfer your emails to another computer.  I did this before from 10.4 to 12.4 and it worked fine.
This time however the emails are not transferring.  All the email accounts are listed but there are no folders or emails.  I have tried it several times in case I made a mistake.  
I tried:
1) Copying the files inside my 12.4  profile into a newly created 16.4 profile.
2) Copying my old profile into the ".thunderbird" folder.
3) Booting to and zipping the entire 12.4 ".thunderbird" folder and then booting to 16.4 and unzipping the ".thunderbird" directory.

Same results, accounts listed in the left side folder pane but no emails.  The accounts are listed in the accounts section.

I am multi-booting so I know the emails are there.
Thunderbird: 38.7.2
Linux SoFl-Desktop 4.4.0-22-generic #39-Ubuntu SMP Thu May 5 16:53:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Thank you
It has been a long time since I have been here.

---

### Post by $yl9pAR%t on 2016-05-16
I did it in the past two ways (always successfully):

1. After fresh install, you can start Thunderbird and close it after start, this way you have created .thunderbird directory in your home directory. Next, you should navigate to your .thunderbird directory and remove its content (Crash Reports directory, xxx.default directory and profiles.ini file). Now, you should paste here (to empty .thunderbird directory) xxx.default directory and profile.ini file (crash reports is unimportant here).

2. Second way (I did it exactly in Ubuntu MATE 16.04), after fresh install before starting Thunderbird paste (or copy) whole your .thunderbird directory (from 12.04) to your 16.04 home directory and start Thunderbird.

Your description is rather short so I am not sure if you did it exactly this way, I mean not starting Thunderbird before copy your old .thunderbird directory to your home directory.

---

### Post by SoFl W on 2016-05-16
Yes I tried that, I also tried that, starting thunderbird so that creates a default profile.  I also used "thunderbird -profilemanager" from the terminal   It sort of works, just the mail is missing.

---

### Post by SoFl W on 2016-05-20
Old system:
[IMG]https://i.imgsafe.org/ec85dda.jpg[/IMG]


New Install
[IMG]https://i.imgsafe.org/ef80b44.jpg[/IMG]


The accounts are there but the emails are not.

---

### Post by vanadium on 2016-05-20
If it concerns IMAP mail accounts, do you see errors when logging into the account? Mail of IMAP accounts is stored on the server. You should see that back after successfully logging in, even if you did not copy the mails from your previous installation of Thunderbird. Locally stored IMAP mail merely serves as a cache.

If it concerns POP mail accounts or locally backed up mail, do you effectively see the files containing your email in the thunderbird profile? Your mail is stored under ./thunderbird/########.default/Mail/Local Folders. If the files are there, but you do not see the mail in thunderbird, then it might be a permission problem.

---

### Post by SoFl W on 2016-05-20
I have both Pop and imap accounts, neither work.  I copied the ####.default directory and the contents over and it does not work.  I 774 the ".thunderbird" directory.  The accounts are there so it is reading the accounts, it just isn't finding the mail.

Edit:  I tried creating a link and that did not work either.  It works fine if I boot to the old distro.  I don't think this makes sense but could it be a gnome vs mate issue?

---

### Post by X-RED_Tech on 2016-05-20
Not sure if you tried that already but I would do it again just in case: Method 2 of post#2 -> Delete .thunderbird and just copy the whole .thunderbird folder from the working system.
Messing with permissions and/or just copying selected folders/parts is usually a recipe for what you're experiencing and a lot of other problems.

---

### Post by vanadium on 2016-05-20
+1. Another possible reason why it would not work could be a change in file formats between the Thunderbird version on 12.04 and that of the version coming with 16.04, although I do not expect this.

---

### Post by SoFl W on 2016-05-20
I have deleted and copied numerous times.  
[[COLOR=#000000]vanadium[/COLOR]]("http://ubuntuforums.org/member.php?u=268902")[COLOR=#000000] , thank you but I kept up with the upgrades with Thunderbird.

I tried creating a symbolic link to the old thunderbird directory hoping it would just pick it up, same results.  It seems like it isn't finding the mail[/COLOR]

---

### Post by SoFl W on 2016-05-20
Checkingthe error console:
I sent a message to one of my email accounts and tried "retrieve messages", this is the error:
Timestamp: 05/20/2016 03:40:19 PM
Error: NS_ERROR_ILLEGAL_VALUE: Component returned failure code: 0x80070057 (NS_ERROR_ILLEGAL_VALUE) [nsIMsgIncomingServer.getNewMessages]
Source File: chrome://messenger/content/mailWindowOverlay.js
Line: 2719


I restarted Thunderbird, these are the errors:

------------------------------------------
* While registering XPCOM module file:///usr/lib/thunderbird/components/libdbusservice.so, trying to re-register CID '{75a500a2-0030-40f7-86f8-63f225b940ae}' already registered by <static module>.

*Failed to load native module at path '/usr/lib/thunderbird/components/libxpcomsample.so': (80004005) /usr/lib/thunderbird/components/libxpcomsample.so: cannot open shared object file: No such file or directory

*Could not read chrome manifest 'file:///usr/lib/thunderbird/extensions/%7B972ce4c6-7e08-4474-a285-3208198ce6fd%7D/chrome.manifest'.

*Timestamp: 05/20/2016 03:42:28 PM
Warning: Expected end of value but found '#F7F6F5'.  Error in parsing value for 'font-size'.  Declaration dropped.
Source File: file:///home/walt/.thunderbird/js6nlw3b.default/chrome/userChrome.css
Line: 15, Column: 16
Source Code:
font-size: 12px #F7F6F5 !important;

*Timestamp: 05/20/2016 03:42:28 PM
Warning: JavaScript 1.7's let blocks are deprecated
Source File: chrome://morecols/content/utils.js
Line: 426

*Timestamp: 05/20/2016 03:42:29 PM
Warning: Use of Mutation Events is deprecated. Use MutationObserver instead.
Source File: chrome://calendar/content/widgets/calendar-widgets.xml
Line: 496
---------------------------------------------

---

### Post by vanadium on 2016-05-20
Perhaps you should try moving your thunderbird profile out of the way (rename it to .thunderbird_old), start thunderbird so it creates a fresh profile. Then copy your email from the "Local Folders" to the "Local Folders" of the new profile. Chances are you will now see your mail, although you will have to reconfigure your accounts. Something else may have gone havoc in your old profile.

---

### Post by SoFl W on 2016-05-21
Thank you for your suggestions and help.  I did try that and it did not work.

I just tried:  cp -Lr [OLD LOCATION] [NEW LOCATION]  It did not work.   

I was thinking there is a file for the mail database that has a relative link.  It can't find the path in the new install.

---

### Post by SoFl W on 2016-09-03
I had given up on this, today I decided to give it one more try.  The problem was the "local directory" option in the 'Server Settings" of the 'Account Settings' was pointing to the old (non-existent) directory.

During this struggle the original drive had failed so I figured any chances to get this resolved were lost.  Once I corrected the path to the current drive it started to load messages from the current file and download new messages from the server.  A few small problems, small corruptions in the folders but everything seems to be working.
 
To anyone else unfortunate to have this problem check to see if the program is pointing to the correct location of the file.  Check account settings ->Server settings ->local directory/

---

### Post by oldos2er on 2016-09-04
I'm glad you were finally able to resolve this problem. Could you please mark your thread 'Solved' under Thread Tools at the top of the page? It will help others who might be having the same problem. Thanks.

---

