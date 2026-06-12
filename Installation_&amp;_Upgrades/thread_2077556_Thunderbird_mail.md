---
title: "Thunderbird mail"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by jronc on 2012-10-28
I have installed Thunderbird into Ubuntu 12.04. I used my existing mail accounts icloud and gmail as my existing accounts. Everything worked fine. I was able to read and send mail using Thunderbird. However, after I shut the computer down and later turned it on, Thunderbird was asking me in the first screen if I wanted to use my existing mail accounts or to get a new mail address. It did not retain the account data that I had entered for the above two email accounts. 
I entered the data again, shut the computer down and again Thunderbird did not retain the data for my two existing mail accounts.

Is this normal behavior? If not why is it dropping the account information for the two existing mail accounts? Thank you in advance for any assistance you can give me.

---

### Post by Frogs Hair on 2012-10-28
Hello and Welcome

This is not normal behavior and I don't know why it is not remembering the data. It is possible that there was an error when the profile was created. 

When the pop up appears close it and go to the application menu on the top panel and use Edit >  Account Settings and see if you account/s information are listed.  

If not use Account Actions in this window to setup your accounts. A new profile can be created by deleting the .thunderbird folder in home hidden folders. Use Ctrl + H to find it.

When  Thunderbird is opened again a new folder will be created.You would lose everything in that folder but have new profile.

If you do this enter your account info as I described above and do not use the pop up window.

---

### Post by jcarrete on 2012-10-28
Hi jronc,

While you find a solution, I suggest you copy the folder .thunderbird with an alternate name after entering the data once again.  You could save it with a name such as .thunderbird.bak and then re-start to machine.  This may eventually save you having to re-enter all the server data while you debug the issue.

Note the date and time in .thunderbird, it should not have changed after the restart (it will, however, change the moment you re-open Thunderbird).

Cheers,

jcarrete

---

### Post by jronc on 2012-10-29
Thank you for coming back so quickly. Unfortunately, This could not help Thunderbird from its bout with amnesia. I have given up trying to get it to work. I will just use the browser to open the mail accounts directly. Again, thanks for you assistance.

---

### Post by Frogs Hair on 2012-10-29
Evolution is in the repository which was the default client prior to Thunderbird if you want a mail client.

---

### Post by jronc on 2012-10-31
Much to my chagrin, I realized that I was logging in as a guest not as myself. Thunderbird was doing exactly what it was supposed to do and drop all account data from a guest session. Once I realized this and logged in on the log in screen as myself, Thunderbird ran perfectly showing the two existing accounts that I had entered earlier. 

I guess that I am showing my age, senior moment and all. But, I thought that I would take my medicine and share the solution in case another noob like me has this "problem" with Thunderbird and this will hopefully help them.
I had set up a password for the sign in but when I had inadvertently checked guest, I wasn't awake enough to realize that it should not be letting me log in without the password. I thought that when I set it up, I screwed up and didn't require as password startup. Oh, well, like I said senior moment.

---

