---
title: "no POP3 option in Thunderbird - Lucid Beta 2"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JoeMac42 on 2010-04-12
I just installed Lucid Beta 2 and noticed that default e-mail changed from Evolution to Thunderbird.  Thunderbird did not successfully import my username or server settings from Evolution.  Worse yet, there is no option that allows selection of POP3 for incoming mail in Thunderbird - it appears to only allow IMAP.  Manual configuration grays out the ability to change the incoming mail server type and no option is given to choose POP3 in the automatic configuration.  I couldn't really find a fully "manual" means to set up my account.  I would like to give Thunderbird a try, but I've gone back to Evolution until I can find a solution for those of us stuck with POP.

---

### Post by JoeMac42 on 2010-04-12
I just tried importing my Evolution settings into Thunderbird.  On the second page of the import wizard, there is a prompt to select the application to import preferences from and there are no options given.  I would think that considering the number of folks using the default e-mail in previous Ubuntu distributions we would want this import tool in Thunderbird to at least be capable of importing settings from the previous default e-mail program (Evolution).  It appears to be completely broken.  Until the import function is fixed, I wouldn't recommend switching default e-mail clients - the end result could leave plenty of new and novice users "high and dry" with respect to their e-mail accounts.

---

### Post by rogerdean on 2010-04-12
the default email program hasn't changed - it's evolution. thunderbird isn't installed by default, so i suspect you might have chosen to install it somehow...?

---

### Post by Didius Falco on 2010-04-12
> **JoeMac42 said:**
> I just tried importing my Evolution settings into Thunderbird.  On the second page of the import wizard, there is a prompt to select the application to import preferences from and there are no options given.  I would think that considering the number of folks using the default e-mail in previous Ubuntu distributions we would want this import tool in Thunderbird to at least be capable of importing settings from the previous default e-mail program (Evolution).  It appears to be completely broken.  Until the import function is fixed, I wouldn't recommend switching default e-mail clients - the end result could leave plenty of new and novice users "high and dry" with respect to their e-mail accounts.

I found a bunch of solutions by doing a quick google. The one below seemed the easiest to follow for mail importation.

[http://people.uleth.ca/~daniel.odonnell/Blog/importing-email-from-evolution-to-thunderbird]("http://people.uleth.ca/%7Edaniel.odonnell/Blog/importing-email-from-evolution-to-thunderbird") 

Here is a guide from the help system here in the Ubuntu help system:

[https://help.ubuntu.com/community/MigrateEvolutionToThunderbird](https://help.ubuntu.com/community/MigrateEvolutionToThunderbird)

This one tells you how to convert your address book into an importable file type, and offers other links that should help in the process.

I have Thunderbird 3.0.4, and I have pop3 available as a choice for email accounts, so I'm not sure what to tell you about that. It could be that it didn't install fully and needs to be reinstalled. Couldn't hurt, might help.

Of course, If you want to stay with Evolution, just purge Thunderbird...

I hope you find this useful,

Regards,

Didius

---

### Post by emarkay on 2010-04-12
The annoying thing about these "upgrades" (Thunderbird 3) is that they add all kinds of unwanted and unneeded crapola "to make life easier".  TB3 "tries" to auto configure your email configuration by looking up your ISP/Vendor by default - not only do I not trust things like this, but I don't want any "template" setting up my email.

IMHO, this just continues the trend of "Idiocracy". 

If you know your settings, you can (luckilly, still) enter this manually.  May want to confirm your settings...

---

### Post by Cavsfan on 2010-04-12
When I first went to create my account with Thunderbird, I couldn't find any POP3 option either. 
The assisted setup kept wanting to use a "secure" connection and my ISP does not use a secure connection, 
so I quit that and played around with it for a few minutes and found the POP setting.
Viola! You just have to do some digging with the account settings and you should be able to get it to work.

---

### Post by JoeMac42 on 2010-04-12
I think what happened is that cairo-dock placed a dock applet for Thunderbird into my dock by default.  I had trouble getting the settings for my AWN panel to work in Lucid (I could add applets but not delete them) so I switched to cairo-dock instead.  When I first searched the forum, I saw polling on whether or not Thunderbird should replace Evolution and thought maybe that had happened.  I guess not.  Good thing, I think.

I did do a bit of digging around and found that I could delete my account in Thunderbird, create a new one and switch to manual set-up to get to an option for POP.  Once the account is created by the automated setup as IMAP, there doesn't seem to be any way to switch it to POP.  Thunderbird's automated setup is an abomination.

In the end, I will probably just stick with Evolution since that has worked fine for me for a couple of years now.

---

### Post by bennachie on 2010-04-12
Thunderbird 3 is a good piece of kit, but the (well-intentioned) approach to establishing your basic email settings is nothing but a pain in the neck for even a moderately competent user. One can only hope that the developers will see the light, and offer users the option of proceeding straight to a traditional manual install.

However, until that epiphany occurs, if you simply stop the search process in its tracks, you can edit the settings that Thunderbird was exploring at the time, then proceed to a manual installation to tidy up the loose ends.

You'll have to go through the same process for each mailbox, though ...

---

### Post by Cavsfan on 2010-04-13
JoeMac42, that is exactly how I got through it. I had to delete the account and set it up manually.
But, I do like Thunderbird and will keep it.

One thing about the version 3 update when it came down, it had the emails opening up in the same window. 
I didn't like that and went back to 2.x version and then I found there is a setting somewhere that 
controls whether a new email opens in the same window or it's own.
So, I like the newer version. I have a lot of rules (like 15-20) setup for my wife that took a lot of time to make 
(putting this type of email in this folder, etc.).
Thunderbird has an exporter that will export everything: emails, contacts, rules, folders, etc. 
So, in a matter of minutes, you can backup all of your email and everything custom you have.
That alone was enough for me to keep it! Especially when you never know when you might have to do a clean install.

---

