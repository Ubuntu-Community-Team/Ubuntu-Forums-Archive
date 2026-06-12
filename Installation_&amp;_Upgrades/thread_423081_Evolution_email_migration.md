---
title: "Evolution email migration"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by RichJacot on 2007-04-25
Hello,

I was using evolution 2.6.1 ( I think ) on dapper.  I copied off my .evolution directory and did a fresh install of edgy.  I now have evolution 2.8.1.  I "thought" I could just copy my .evolution dir back into the new home dir and I'd be all set.  Needless to say, no such luck.  Now no matter what I do I can't get my old emails into my new evolution install.  ](*,) :confused: 

I've copied my .evolution/mail/pop/xx.xx@pop.gmail.com dir in the same place on the new install and still nothing.  

Does anyone have any ideas?  

TIA

---

### Post by jpatton on 2007-04-25
When I did an upgrade from 6.10 to 7.04 I had uploaded my entire .evolution folder to my local ftp server, and then downloaded it back after. But all my mail is located under ./evolution/mail/local which makes me wonder if maybe you copied the wrong directory?

Now, unless you told gmail to delete mail that was downloaded, you can go back in and turn off pop access and then turn it back on, and all that lovely mail will come back in.

Hope this helps :)

---

### Post by RichJacot on 2007-04-26
I'm going to try putting may pop mail dir in .evolution/mail/local to see if they show up in my inbox then.  I have a questions about turning pop off and back on again.  What does that do?

I'll let you know how it goes....

---

### Post by jpatton on 2007-04-26
> **RichJacot said:**
> I'm going to try putting may pop mail dir in .evolution/mail/local to see if they show up in my inbox then.  I have a questions about turning pop off and back on again.  What does that do?

I'll let you know how it goes....

do you mean from gmail? if you want to make sure that you get all the mail you had before you need to set it to all mail, i think it defaults to mail from now on or something like that. setting it back to all you will get EVERYTHING...lol..that may be good for you i don't know, i never delete stuff so for me it was like 5,000 emails!

but like i said earlier, that will only work if you DIDN"T have it set to delete mail that was downloaded from pop. i think that also is if you didn't have your client set to remove messages from the server as well. if you go to all mail in gmail and see stuff, then you should be gold.

let me know what happens.

---

### Post by RichJacot on 2007-04-27
Okay, here's what I've discovered.

I did as you mentioned and downloaded all of my new gmail mail and it worked fine.  It appears to have only downloaded emails that were new since I last used evolution on the dapper system.  I even turned off and back on my pop settings before doing it.  What I notice is that .evolution/mail/local has the folders (i.e. Inbox etc..).  If I vi that file I can see the emails recently pulled down.  I also notice that .evolution/mail/pop/xx.xx@pop.gmail.com/cache has alot of dirs. with emails in them too???     What appears to be my issue is, how do I get the emails from the .evolution/mail/pop/xxx/cache dirs to be indexed or loaded into the .evolution/mail/local/Inbox (or whatever folders)?  That's the piece I appear to be having trouble with.

I had a number of folders with a lot of emails sorted into them.  I'm hoping there is a way to get the recovered.  I say recovered now because it appears it not a simple migration any longer.  ;) 

Thanks again...

---

### Post by jpatton on 2007-04-27
hmmm...i'm not really sure, as i told you earlier, when i backed up my mail, i just copied the entire .evolution folder to my ftp server, and after the upgrade downloaded it back down before i opened evolution. since evolution is part of gnome, have you checked on any of the boards from gnome's website? i think they have some, not sure though.

the reason i grabbed the entire directory structure was for the same reason, all my mail is sorted into various folders, and i had noticed while browsing that it appeared there was stuff kind of everywhere.

good luck, and if you get a response from the folks at gnome, post it here because i would be really interested in how that turns out. or it could be that someone here in the community might be able to help as well, have you searched any of the other forums?

---

