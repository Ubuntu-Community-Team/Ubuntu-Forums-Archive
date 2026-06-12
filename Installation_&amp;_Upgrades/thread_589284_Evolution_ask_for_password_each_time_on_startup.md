---
title: "Evolution ask for password each time on startup"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by stefangachter on 2007-10-24
Hi, I deleted 7.04 and installed 7.10, but I reused my evolution configuration and folders. Now, each time I startup evolution, it asks me for the password of the POP mail server, because it has  a problem to send the username or so:

---
Unable to connect to POP server mail.****.**.
Error sending username: 

Please enter the POP password for ******* on host mail.****.**
---

However, even if I enter the correct password, evolution does not recognize it and keeps asking me. If I cancel the dialog, however, I can send and receive email as usual. So, I don't understand what the problem is.

I tried to delete all passwords (File -> Forget Passwords), but after entering the passwords anew, the same dialog box appears every time.

How can I get rid off this dialog? What might cause the problem?

Thanks for any hint. Stefan

---

### Post by Handssolow on 2007-10-24
Looks like I've got the same problem after upgrading from Feisty to Gutsy. Every time I open Evolution mail I get a  box saying it can't connect and asks for my pop password despite a row of black dots showing it's remembered my password. I've just discovered that if I close the box I'm still able to send and receive emails.
I tried removing Firestarter but it made no difference so I've reinstalled it.

Why does the password dialogue box keep appearing?

---

### Post by bandyo on 2007-10-24
I have the same problem. After the upgrade from 7.04 to 7.10, when I open Evolution I get the password dialog for all my accounts. Entering the passwords don't work. Only Cancel works. Once canceled Evolution can send and receive mail just fine.

---

### Post by stefangachter on 2007-10-25
So, now we are three having the same problem... wondering, if somebody is out there knowing a solution, or if we have to declare this as a bug...

---

### Post by Steve1961 on 2007-10-25
Same thing happening here

---

### Post by drewlake on 2007-10-25
> **Steve1961 said:**
> Same thing happening here

The missus is having the same problem. I've not had chance to see what the problem is, but it's odd that I don't get the problem when I'm using the same PC as a different user. I'll have a look tonight and see what I can dig out.

---

### Post by chargersfan39 on 2007-10-26
I am having the same problem - its quite annoying

---

### Post by GrumpyBob on 2007-10-26
I haven't had this with my upgrade (I'm using an MS Exchange mails erver), but have in the past when the account details set in preferences were wrong.  Perhaps the problem lies there?

Robert

---

### Post by Handssolow on 2007-10-26
I've looked at my Preferences in Evolution Mail and found nothing obvious that needs changing. It's not that I can't send and receive emails it's just that the password box keeps appearing every time I open the application and  have to keep closing again.

Just another Gutsy Bug like the loss of the keyboard's £ sign?

---

### Post by stefangachter on 2007-10-26
Same for me... I use exactly the same account settings as with 7.04. So, this might not case the problem.

---

### Post by rogerdean on 2007-10-28
same story here. i'm using my 7.04 profile as backed up and restored by the third party utility evolbck

i have 3 pop accounts enables. seems as if i cancel the password request for the first account quickly, it then asks me for the second. but if i ignore it for a while and then cancel it, it doesn't. suggests that there is some sort of time lag before evolution can correctly manage a password...?

---

### Post by xbytes on 2007-10-28
I have same problem here also! occasionally it works but generally not!! :confused:

---

### Post by dagvei on 2007-10-29
Sorry, did not see this thread; I started a new one about the same issue : YES, I am also prompted for passwords on every single start-up of Evolution. It is quite annoying, so I have gone back to good old Thunderbird, that seems to be a far better programme anyway, although the lack of all Evolution's features.

---

### Post by nitrobruno on 2007-10-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/evolution/+bug/140460&quot;]https://bugs.launchpad.net/evolution/+bug/140460](https://bugs.launchpad.net/evolution/+bug/140460&quot;]https://bugs.launchpad.net/evolution/+bug/140460) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

The bug has been reported: 
[https://bugs.launchpad.net/evolution/+bug/140460]("https://bugs.launchpad.net/evolution/+bug/140460")

A couple of temporary solutions are given to avoid the problem: for example choose a folder different from inbox before closing evolution.

---

### Post by rod40cool on 2007-10-31
I too found this after doing fresh install of 7.10 and then restoring my saved 7.04 Evolution mailbox files and settings.

Another way to avoid the error on start of Evolution is to turn off automatic checking of pop3 mailboxes and use the "Send/Receive" button manually - not great I know.

---

### Post by Handssolow on 2007-11-13
Looks like this bug has been solved by one of today's 20 plus updates.
My thanks to those concerned with this.

---

### Post by Handssolow on 2007-11-13
Sorry but I posted too soon. I've just rebooted and the Evolution password error is still present.

---

### Post by superyounan1 on 2007-12-09
yeah, i guess i'm a little late to this thread, but this bug has been annoying me too. The suggested temp fixes listed in teh launchpad comments dont work for me, but they might for you

specify the email component when launching (no difference for me)```
evolution --component=mail
```

start in offline mode (for me this causes an error that says it could not contact the pop server, replacing one annoying pop up with another, but what they hey, it works for other people)
```
evolution --offline
```

i backed everything in my .evolution directory in feisty, clean install to gutsy and imported it with the new evolution

---

### Post by stefangachter on 2008-01-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/evolution/+bug/140460](https://bugs.launchpad.net/evolution/+bug/140460) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There is now a suitable workaround, see here:

[https://bugs.launchpad.net/evolution/+bug/140460](https://bugs.launchpad.net/evolution/+bug/140460)

Move all your mails from the inbox to another folder. Then close Evolution. Goto ~/.evolution/mail/local/ and remove all files beginning with Inbox (in my case there were six files). Now you can start Evolution again and move the mails back to the inbox. The bug disappeared.

---

### Post by Handssolow on 2008-03-06
Just to mention that I've still got this bug despite downloading the latest Evolution updates today. 

If Evolution is opened having been previously left on Inbox, the password dialogue box opens showing a row of my previously entered password. I then press cancel and usually send/receive after which Evolution behaves normally. Closing Evolution on something other than inbox avoids seeing this bug when Evolution is next re-opened..
I haven't followed  the workaround which involved moving various  inbox files. Disabling the automatic checking of new emails also stops the bug's appearance.

Any other solutions?

---

### Post by Mad_Max_1412 on 2008-03-12
I had exactly the same issue.  If Evolution opened with the inbox selected, then I got the prompt.  If it opened with any other folder selected, it connected and downloaded email fine.

The above mentioned work around (ie moving emails from inbox etc) worked for me.  Took me about 2 minutes to implement, including moving emails back to inbox and deleting the temporary folder I created.

---

### Post by ubsessed on 2008-03-12
Hello (haven't posted again so I am not sure that this is the thread that I should be posting)

Evolution asks for passwords after hanging itself (and sometimes the system) for some minutes. 
Then it asks for passwords on all your accounts and unhangs. 
When you make any move (selecting another folder maybe) it hangs again and again asks for passwords at the end of it. When you make the mistake of pressing ok on the password dialogue it hangs again .....and again and again. 
My mailing system was useless.  
Couldn't find a solution so I was compelled  to evolve to thunderbird and move the mail to it.  
The link that did the trick of moving is [http://www.ubuntugeek.com/how-to-export-your-mails-from-evolution-to-thunderbird.html](http://www.ubuntugeek.com/how-to-export-your-mails-from-evolution-to-thunderbird.html).



](*,):mad::confused:

---

### Post by Handssolow on 2008-03-16
I followed the instructions and  the bug seems to have disappeared, thanks everyone. This time I created another email folder and moved all my inbox emails to this new folder before I closed Evolution. Rather than deleting any Inbox files as suggested,  I renamed them  and temporarily moved them to Desktop. After restarting Evolution the inbox files were recreated but I replaced them with those on my Desktop after I had reverted their names back to their originals.

The only hitch was when I restarted Evolution Send/Receive was greyed out then I realised that the "Work Offline" was ticked.

But what a strange Bug!

---

### Post by Mike-97470 on 2008-04-08
Of course thanks to the poster of the Inbox fix.  Note that the same bug exists if you close Evolution with another folder selected (other than Inbox).   I suppose the same fix works for the other folders....

---

