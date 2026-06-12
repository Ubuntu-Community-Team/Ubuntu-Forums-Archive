---
title: "No release file for xenial ? Repository missing?"
date: 2017-03-25
forum: Installation &amp; Upgrades
---

### Post by schnuckenack2 on 2017-03-25
Hello

when executing "apt-get update" I receive two error or warning messages respectively:

#1
> W: The repository 'http://extras.ubuntu.com/ubuntu xenial Release' does not have a Release file

#2
> Fehlschlag beim Holen von [http://extras.ubuntu.com/ubuntu/dists/xenial/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/xenial/main/source/Sources)  404  Not Found [IP: 91.189.92.152 80]

In the browser there really is no folder xenial/, there only are folders precise/, quantal/, saucy/, trusty/, utopic/

Halp anyone?

Yours, Schnuckenack

---

### Post by howefield on 2017-03-25
I'd suggest removing the entries for the "extras" repository from your sources.list file which you should be able to do from the Software & Updates application and then enable the Partners repository from the *"Other Software"* tab. I believe that's the repository you need for Xenial.

---

### Post by schnuckenack2 on 2017-03-25
Thank you howfield !

---

### Post by howefield on 2017-03-25
> **schnuckenack2 said:**
> Thank you howfield !

You're very welcome, does this mean that your query is resolved ?

If so, feel free to mark the thread as such :)

---

