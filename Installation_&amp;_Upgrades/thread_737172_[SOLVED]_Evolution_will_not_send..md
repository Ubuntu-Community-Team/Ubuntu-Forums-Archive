---
title: "[SOLVED] Evolution will not send."
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by lawentzel on 2008-03-27
I have setup three email accounts.  My system will not send emails either from Evolution nor from Thunderbird.  I am getting an error which reads "RCPT TO <emailaddress@whereever.com> failed: Transaction failed".

I have just finished reformatting my computer and reinstalling Ubuntu 7.10 along with the 200+ updates and am still getting the same errors.

The accounts I have setup are an internal work email account, GMail, and SBCGlobal.net.  Our work does have a filtering program, if I use the regular network cable, but via a wireless connection it is completely open.  So, that isn't the issue.

Any help in this matter would be greatly appreciated.  Thank you.

BTW: I have looked at the forum and found a number of people with the same issues and none of them have been able to resolve this.  One guy resorted to restoring a back up, which is an option not available to me.

---

### Post by lawentzel on 2008-03-27
Being one to not like technical things not working for me.  I kept digging into this after I posted this problem.  I found the answer to this issue while reading a similar problem on a PHP post.  This should take care of this problem for everyone!  (Notice my confidence?)

All I had to do was add the person to my contact list.  That's it.  Problem solved.  It has to do with the data that is being sent and my guess is there is a bug in there somewhere.  The fact that Ubuntu 7.10 comes with version 2.12.1 of Evolution and they are up to 2.22 leads me to believe it has been addressed and fixed.

So, all of you out there getting the similar problem try adding the person to your contact list.  There is an option under Mail Preferences, under the Automatic Contacts tab where you can select the program to "Automatically create entries in the addressbook when responding to mail".  I suggest checking it.

---

