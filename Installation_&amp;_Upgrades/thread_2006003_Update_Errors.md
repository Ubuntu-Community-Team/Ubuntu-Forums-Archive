---
title: "Update Errors"
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by Rex Bouwense on 2012-06-18
Been awhile since I asked a question.  I was manually doing an update through the terminal using apt-get and I got errors.  I have posted a screen shot.  I have not installed or uninstalled any software other than the kernal update last week I believe.  I was getting updates regularly via apt-get and the update manager.  Now what do I do?

---

### Post by Old_Grey_Wolf on 2012-06-18
For one of the errors, you are missing the GPG key. To get it enter theses commands in a terminal. ```
gpg --keyserver keyserver.ubuntu.com --recv A8AA1FAA3F055C03
gpg --export --armor A8AA1FAA3F055C03 | sudo apt-key add -
```

It may fix another error you are getting.

The screenshot made it difficult for me. I couldn't just copy and past the GPG Key from a terminal output in your post and pasted into my response. I had to try to enter the GPG Key I was seeing from the screenshot. I hope I didn't miss a Hex value.

---

### Post by Rex Bouwense on 2012-06-18
Thanks for your response.  I copied and pasted the code and ended up with the errors in screen shot.

---

### Post by Old_Grey_Wolf on 2012-06-18
Try these commands ```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
exit
```

---

### Post by Rex Bouwense on 2012-06-19
That did the trick.  Drinks on the house.  Thank you Old_Grey_Wolf.  In the many years that I have been using Ubuntu and then Lubuntu, that has never happened to me.  I got it bookmarked just in case.

---

### Post by Old_Grey_Wolf on 2012-06-19
I'm glad it worked. Yesterday I was only getting a 50% success rate at solving problems; so, it makes me feel a little better. LOL

---

### Post by Rex Bouwense on 2012-06-19
Hey OGW, 50% is better than what I was doing yesterday.:popcorn:

---

