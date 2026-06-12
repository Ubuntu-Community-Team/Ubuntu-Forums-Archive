---
title: "[SOLVED] what is my key id in this screenshot?"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by lukydude on 2008-05-31
its needed for launch pad

---

### Post by Dougie187 on 2008-05-31
I believe it is
"E6E1 CB56 8964 A05A B980 F6C9 6088 BF62 4F1A1C96"

If you want someone to be able to import your key into their keyrings try this
```
gpg --export --armor <your e-mail address> > key.gpg.asc
```

More can be found here.
[http://nmlug.org/faqs/gen-gpg-key.html](http://nmlug.org/faqs/gen-gpg-key.html)

---

### Post by lukydude on 2008-05-31
> **Dougie187 said:**
> I believe it is
"E6E1 CB56 8964 A05A B980 F6C9 6088 BF62 4F1A1C96"

If you want someone to be able to import your key into their keyrings try this
```
gpg --export --armor <your e-mail address> > key.gpg.asc
```

More can be found here.
[http://nmlug.org/faqs/gen-gpg-key.html](http://nmlug.org/faqs/gen-gpg-key.html)
I need to upload them first but i dont know what the id is, it says upload them but then hen i try it (figured out it' the 5CF11800 bit) but still not working (screenshot) if i still have no luck could somebody remotely use my pc to help?

---

### Post by Dougie187 on 2008-05-31
Instead could you maybe link to the site that is giving you issues? or asking for your key? Or take a screenshot of that? That might help as well.

---

### Post by lukydude on 2008-05-31
cant you just remotely use my pc anyway attached look @ all 3

---

### Post by lukydude on 2008-05-31
well?

---

### Post by tact on 2008-05-31
your key id is 4F1A1C96

---

### Post by tact on 2008-05-31
I just searched the keyservers and cannot see your key there.  So either you have not successfully uploaded it yet or you uploaded to a different server and its not yet been sync to all servers.

your key ID is 4F1A1C96
that key's fingerprint is 6E1 CB56 8964 A05A B980 F6C9 6088 BF62 4F1A1C96

To get it uploaded to a key server using terminal:
```
gpg --keyserver keyserver.ubuntu.com

```
Followed by:
```
gpg --send-keys

```

Or if you want to use a GUI...  
-Click on Applications>Add/Remove
-In the search box at top right type in:   seahorse
-If it is already ticked, already installed skip the next step
-tick the box beside the application "Passwords and Encryption Keys" and wait while it installs.

After its installed:
Applications>Accessories>Passwords and Encryption Keys

You should see your key listed.  If not you have to import it. So click on Key>Import and navigate to where your key is stored and import it.

(It looks to be /home/luke/.gnupg where your keys are...if you cannot see the .gnupg folder in the files dialog its because its a hidden folder.  So right click and tick the box "show hidden files")

Once the application "Passwords and Encryption Keys" is installed and your keyrings imported... you will see your Key ID and fingerprint info.  

You will also be able to upload your key to a keyserver, even select the keyserver etc...

---

### Post by lukydude on 2008-05-31
thats all done ~ thanks.

---

### Post by tact on 2008-05-31
> **lukydude said:**
> thats all done ~ thanks.

Well thats good.  I did a search and see your key is available on the server so you were successful.

Cheers

---

