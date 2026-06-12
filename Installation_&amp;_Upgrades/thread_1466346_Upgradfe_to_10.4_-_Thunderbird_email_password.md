---
title: "Upgradfe to 10.4 - Thunderbird email password"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by wcorey on 2010-04-30
I upgraded my 9.10 desktop to 10.4. In the process my Thunderbird client lost the ability to get email. I get the error message "Error getting email password". New in Thunderbird 3 is it keeps email passwords tucked away out of site. I have my email repository on my NAS and now email is unable to fetch.

---

### Post by Toftevall on 2010-04-30
When I upgraded I had to put in all the info (password, servers...) again. **Cant find my old e-mails!** Are they lost forever or are they just hidden somewhere? 

Pls help if you can, Martin

---

### Post by wcorey on 2010-05-01
If you used the same name/email address I suspect they are gone. as the repository for the emails are kept in a funky subdirectory name pointed to by profile.ini under .mozilla-thunderbird which is a symlink to .thunderbird in your home dir. In that there is a signons.sqllite and secmod.db. I bet that is where they are stored. I bet the linkage to these is by account name or email address so you likely zeroed them out....but follow the link to verify, You should see your folders and underneath them large files which are your emails, to the best of my knowledge.

However, the more I think about it the more brain dead the thunderbird upgrade was to effectively break someone's email. However, in fairness, I suspect this is a Mozilla issue, not Ubuntu issue. I was just hoping someone would have hit this issue, done the heavy lifting on it, and has a simple solution.

---

### Post by wcorey on 2010-05-01
After researching this on the mozilla site it appears the only 'try this' vaguely resembling a solution is to uninstall TB 3 and reinstall TB2. Some people have simply stayed on TB2, presumably because TB3 is broken and others have mucked around with the TB2 files such that they can reinstall TB3 and have it work successfully. 

I uninstalled TB3 and found and downloaded TB2 but could not install it as it needed the version 5 of libstdc++. This, as I recall, was removed as obsolete during the 10.4 upgrade and, in any event, not available on the current Ubuntu repositories. 

So now I am on U10.4 with a completely unusable email system. Given I can't go back to the U9.10 email I am guessing this did just become a Ubuntu bug.

Has anyone else had this problem and has anyone else had this problem and gotten past it?

---

### Post by wcorey on 2010-05-01
I honestly don't know how or why this happened but about an hour after my last post, while I was working on a new 10.4 Server image, I caught out of the corner of my eye an email fetch from the TB3 instance I left running. Lo and behold, it was working. I had recently downloaded 2 package updates that I don't think were related...but who knows.

I just wanted to let folks know it was working now.

---

