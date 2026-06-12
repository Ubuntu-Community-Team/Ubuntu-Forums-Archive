---
title: "exclude packages in apt-get"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by jmvidalvia on 2007-03-03
I like to update my xubuntu from terminal using apt-get.
But cdburn is broken for edgy, so i had to install the dapper one.
Now, in every update, apt-get tells me to upgrade cdburn.
How can I tell apt-get "upgrade everything except this..."?
Thank you very much!

---

### Post by kissson on 2008-02-02
push

---

### Post by erfahren on 2008-02-02
I guess that original post is a little old

anyway, you can open Synaptic Package Manager and search for the package you don't want upgraded - highlight it and in Synaptic's menu go to "Package" > "Lock Version"

that will keep it from updating/upgrading

---

### Post by CheckItOut on 2008-02-13
If that isn't working (like in my case) do:

Install wajig with:
apt-get install wajig

Then exclude the package with:
wajig hold <package>

Good Luck

---

### Post by jmvidalvia on 2008-02-13
Great!
That is what I was looking for: locking files via console.
Many thanks!

---

