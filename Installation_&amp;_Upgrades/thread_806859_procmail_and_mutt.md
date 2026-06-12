---
title: "procmail and mutt"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by cssutto on 2008-05-25
Just installed 8.04.

Proccmail will nt post messages to any mail box.

All logs show "MDA returned nonzero status 75 "

The logs indicate that fetchmail sees the message and passes it on to procmail, but then things go wrong.

I also get the message that the procmail.log failed.

The setup I have works perfectly in 6.06.

I have spend several hours on this problem, so help will be appreciated.

---

### Post by andrew.46 on 2008-05-25
Hi,

Can you post the contents of ~/.procmailrc? And can I ask as well the syntax that you use in ~/.fetchmailrc to pass the mail to procmail? My own is:

```
mda "/usr/bin/procmail -d %T"
```

Can I ask as well what program you are using to view the mail? I am hoping that you will say mutt but I will forgive another choice :-).

             Andrew

---

### Post by cssutto on 2008-05-26
I only began using linux about 3 years or so ago and for me, mail was one of the most difficult things I had to learn to use.

So these files were cobbled together, a little at a time over three versions of Ubuntu and two computers.

So even though they are not pretty, the worked like gangbusters in 6.06 so I had no interest in trying to clean them up.

And yes, I do use mutt.

Evolution looks to me like Bill Gates wrote it.

#Default parameters for procmail

VERBOSE=yes
#USR2

#where is our homedir
HOME=/home/claude69694 

# what is the default place to store mail   
MAILDIR=/var/mail/
DEFAULT=/var/mail/claude69694

# Default INBOX
DEFAULT=/var/mail/claude69694



# keep a log
LOGFILE=/var/log/procmail.log    

:0fw
| bogofilter -e -p

:0e
{ EXITCODE=75 HOST }
# file the mail to spam-bogofilter if it's spam.
:0 H:
* ^X-Bogosity: Spam, tests=bogofilter
spam


#this was on line above Bogosity * ^X-Bogosity: Spamtag
#this was on the line above trash * ^X-Bogosity: Yes, tests=bogofilter

#Save family mail in family box
:0: 
* ^TO_Liz Cotton|thenoddinggod|ginny|virginiawood|Virginia S. Wood|Virginia Wood|lizcotton
family

#Topica Mail
:0:
* ^TO [email]Foxhunters@topica.com[/email]|topica|Topica
topica

FOL Mail
:0:
* ^TO_Foxhunters Online
#foxhunters
spam

#Claude's mail
:0:
* ^TO_claude69694
$DEFAULT
'''



 Configuration created Mon Aug 27 19:21:24 2007 by fetchmailconf 1.52 $Revision: 4636 $
set postmaster "claude69694"
set bouncemail
set no spambounce
set properties ""
set daemon 120



set syslog  

#poll [email]claudesutton@suttonmachine.com[/email] with proto POP3 user 'claudesutton@suttonmachine.com' there with password 'xxxxxxx' is 'claude69694' here options fetchall stripcr mda 'procmail -f-'
   


poll suttonmachine.com with proto POP3 user 'claudesutton@suttonmachine.com' there with password 'xxxxxxxxx' is 'claude69694' here options fetchall stripcr mda 'procmail -f-' sslproto '' 
   

mda '/usr/bin/procmail -d %s'

---

### Post by andrew.46 on 2008-05-26
Hi again,

 Thanks for the extra info:

> **cssutto said:**
> I only began using linux about 3 years or so ago and for me, mail was one of the most difficult things I had to learn to use.

So these files were cobbled together, a little at a time over three versions of Ubuntu and two computers.

So even though they are not pretty, the worked like gangbusters in 6.06 so I had no interest in trying to clean them up.

And yes, I do use mutt.


I agree with you that setting up mail in this way can be a complex procedure. I published a couple of pages on just this subject if you were ever interested in comparing notes, one on the [Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=565326") and one on my [own web site]("http://www.andrews-corner.org/mutt.html"). 

> 
# what is the default place to store mail   
MAILDIR=/var/mail/
DEFAULT=/var/mail/claude69694


I wonder if perhaps the problem lies with your default mail spool, particularly if this is the exact setup that you have used before on a different version of Ubuntu and different computers. Are the file permissions allowing you to access it properly? My own default spool is /var/spool/mail/andrew and the permissions are:

```
andrew@skamandros:~$ ls -l /var/spool/mail/andrew
-rw-rw---- 1 andrew mail 0 2008-05-20 11:20 /var/spool/mail/andrew
```

It would be an easy solution if the permissions on /var/mail/claude69694 were incorrect as this could be corrected easily. I wonder as well what the result of the following command is on your system:

```
andrew@skamandros:~$ echo $MAIL
/var/spool/mail/andrew
```

You do not sound keen to "clean up" your config files, and if they work I well understand this, but I believe that the following:

```
MAILDIR=/var/mail/
```

should be:

```
MAILDIR=/var/mail
```

If these 2 small areas do not fix the problem there may be a need to dig a little deeper perhaps.

         Andrew

---

### Post by cssutto on 2008-05-26
Thank you for the help.

I have not been able to correct the problem yet.

I neglected to mention to you, and should have in my first post, that mail.log reports that that it is unable to write to /var/log/procmail.log

I have changed ownership and permissions even to the point of 777 and nothing I have tried seems to work.

I would guess that if procmail can not write to its log, the log will show when I get it working, why procmail can not write to anything else.

---

### Post by cssutto on 2008-05-26
I should have added that I have procmail.log now set with syslog as the lower, since mail.log has syslog as the owner.


It now is:

:/var/log$ ls -l procmail.log
-rw------- 1 sys adm 0 2008-05-26 10:33 procmail.log

---

### Post by cssutto on 2008-05-26
The mail.log error message is that the log message is incomplete

---

### Post by cssutto on 2008-05-26
claude69694@claude69694-laptop:~$ echo $MAIL

claude69694@claude69694-laptop:~$

---

### Post by andrew.46 on 2008-05-26
Hi,

I still suspect that you have a permission and ownership problem. I see that you also do not have your $MAIL variable set either and this might make your life a little easier if set correctly. Following your existing setup try pressing Alt-F2 and type:

```
gksudo gedit ~/.bashrc
```

or substitute gedit for your favoured gui editor and add your MAIL variable as follows:

```

# Sets the Mail Environment Variable
MAIL=/var/mail/claude69694 && export MAIL
```

I should mention that this is a little non-standard as the usual mail spool would be:

```
/var/spool/mail/claude69694
```

but I think that this does not matter too much and would only confuse the issue a little as you would have to alter your other config files as well. With this in place you should see the output reflected in:
```

$ source ~/.bashrc
$ echo $MAIL
```

Now try altering the permissions and ownership of the mail spool as follows:

```
$ sudo chown claude69694:mail /var/spool/mail/claude69694 
$ chmod 660 /var/spool/mail/claude69694
```

For your procmail log rather than try to fix these permissions perhaps you could try to place the log (for the moment) in your home directory. This of course would require the following in your ~/.procmailrc:

```
LOGFILE=$HOME/.procmaillog
```

as well as the actual creation of the logfile:

```
$ touch ~/.procmaillog
```

With any luck your mail should then roar into life again!

          Andrew

---

### Post by cssutto on 2008-05-26
Well, that got the procmail log going.

I did not expect bogo to work because I have not yet had time to set up word lists, etc.

But I did think the messages would go to my mail.

Anyway, here is the log output:

procmail: Executing "bogofilter,-e,-p"
Can't open file 'wordlist.db' in directory '/home/claude69694/.bogofilter'.
error #2 - No such file or directory.

Remember to register some spam and ham messages before you
use bogofilter to evaluate mail for its probable spam status!
procmail: Error while writing to "bogofilter"
procmail: Rescue of unfiltered data succeeded
procmail: Assigning "EXITCODE=75"
procmail: Assigning "HOST"
procmail: HOST mismatched "claude69694-laptop"
From claude69694  Mon May 26 19:01:16 2008
 Subject: Know her from the sexual side how is she inside exactly
  Folder: 								      0
procmail: Executing "bogofilter,-e,-p"
Can't open file 'wordlist.db' in directory '/home/claude69694/.bogofilter'.
error #2 - No such file or directory.

Remember to register some spam and ham messages before you
use bogofilter to evaluate mail for its probable spam status!
procmail: Error while writing to "bogofilter"
procmail: Rescue of unfiltered data succeeded
procmail: Assigning "EXITCODE=75"
procmail: Assigning "HOST"
procmail: HOST mismatched "claude69694-laptop"
From claude69694  Mon May 26 19:01:17 2008
 Subject: test again
  Folder: 								      0

Obviously I have a problem with my hosts file, but it looks to me like it is OK.

claude69694@claude69694-laptop:~$ hostname
claude69694-laptop

---

### Post by andrew.46 on 2008-05-26
Hi again,

 Unfortunately I am not familiar with bogofilter but it seems that at the very least you need to create this required file:

```
$ touch /home/claude69694/.bogofilter
```

But the actual setup of this program is completely unknown to me. Can you send and receive mail now though? Perhaps temporarily disable all your procmail recipes for the moment and just test the basic send / receive of mail.

The HOST error may be related to your procmail-f- line in ~/.fetchmailrc that I have not seen used before. Is this necessary or can you set this sort of thing with the software you use to send your mail, msmtp / ssmpt etc?

    Andrew

---

### Post by cssutto on 2008-05-26
Andrew:

I fixed it when I copied my old wordlist over to the 8.04.

It seems that when bobo could not find the list, procmail quit.

I had thought it would just pass all messages on to my mailbox regardless of whether it had spam.

Thank you for your help.  It was effective and much appreciated.

---

### Post by andrew.46 on 2008-05-26
Hi,

Glad you got it all working again :-)

         Andrew

---

