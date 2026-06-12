---
title: "Evolution error after upgrade regarding mbox"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by kdnoel on 2011-10-15
I am a little unclear as to what is happening... I got the notice from Evolution that email would be converted to another folder and after checking that everything converted I was to remove mbox. I have not done this but hide the localhost section in Evolution.

I now get this error upon sending email.

The reported error was "Failed to append to mbox:///home/kevin/.local/share/evolution/mail/local#Sent: Invalid folder URI 'mbox:///home/kevin/.local/share/evolution/mail/local#Sent'
Appending to local 'Sent' folder instead.".

I just hit Dismiss and all seems OK.

What do I need to do to remedy this condition?

Best Regards

---

### Post by cgarcia on 2011-10-15
You can fix this in the email account properties.

BEWARE : I use evolution in French. So I try to translate labels back in english = it might not be exactely what you will read but it will give you an idea of where to search ;o)

Here is what I have done :
1. go to menu : Select > Properties
2. in the properties window goto the tab : email accounts
3. Select your email account and click : Modify
4. Goto the tab : Defaults
5. select the correct "draft" and "sent" folders

The warning will not appear anymore on sending new emails !!!

Note that it is probably a bug that could be reported to the developpment team ...

Cheers
Christophe

---

### Post by pestucky on 2011-10-16
Thank you.   YOur recommendation worked.  But in the 11.10 installation of Evolution it instructed to delete Mbox after installing.  How does one do that?
Paul

---

### Post by kdnoel on 2011-10-16
Thank you for the solution cgarcia!

I also found that you can delete mbox in the same area.

---

### Post by kdnoel on 2011-10-16
> **pestucky said:**
> Thank you.   YOur recommendation worked.  But in the 11.10 installation of Evolution it instructed to delete Mbox after installing.  How does one do that?
Paul

Paul when you go to edit preferences you will see you email accounts and you will see mbox... highlight it and then use the delete button to the left lower side.

---

### Post by kdnoel on 2011-10-17
Just want to add... I did the upgrade and did not lose any of my messages.

---

### Post by Handssolow on 2011-10-25
> **cgarcia said:**
> You can fix this in the email account properties.

BEWARE : I use evolution in French. So I try to translate labels back in english = it might not be exactely what you will read but it will give you an idea of where to search ;o)

Here is what I have done :
1. go to menu : Select > Properties
2. in the properties window goto the tab : email accounts
3. Select your email account and click : Modify
4. Goto the tab : Defaults
5. select the correct "draft" and "sent" folders

The warning will not appear anymore on sending new emails !!!

Note that it is probably a bug that could be reported to the developpment team ...

Cheers
Christohe

Many thanks cgarcia.

In Evolution here it's
Go to Edit>Preferences and highlight the email account and press edit.
On the Defaults tab page, in the Special Folders section select that you want Drafts in the Draft folder and Sent in the Sent Folder.

In Preferences>Mail Accounts I also deleted the mbox local host account.

---

### Post by indipage on 2011-10-26
Thanks for the advice, worked a treat.

Mind you it wasn't the only thing that was up the spout after a recent ubuntu upgrade. There may be other things needing attention but the first thing I noticed was kdenlive is now unusable because of some MTL conflict

---

### Post by SteveHillier on 2011-11-03
Hi guys,
None of this seems to apply.
When I loaded Evolution today it went through a 'checking folder consistency' and then seems to have got rid of all my old inbox and sent items content.
I don't have anything to do with a 'mbox' issue.
Any other clues?
Steve

---

### Post by David Oxland on 2012-06-13
Same for me. One forgets these things if you don't go there very often.
Thanks

---

