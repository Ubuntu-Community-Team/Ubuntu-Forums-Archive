---
title: "adept always wants to install one package"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by chris_pmf on 2007-06-13
Hello,

my adept update-notifier steadily wants to update one package, but when I open adept to update this package he says there is nothing to update :?

Synaptic also says there's nothing to update.

What's wrong here?

Thanks

---

### Post by chris_pmf on 2007-07-19
no one?

please :(

---

### Post by bagofchickens on 2007-09-03
It took me some time to find the answer in the forums. Just in case other people are hitting dead end here, go to:

[http://ubuntuforums.org/showpost.php?p=1156648&postcount=2]("http://ubuntuforums.org/showpost.php?p=1156648&postcount=2")

or to:

[http://ubuntuforums.org/showpost.php?p=1156670&postcount=7]("http://ubuntuforums.org/showpost.php?p=1156670&postcount=7")

The first one solved it for me (sudo chmod +r /etc/apt/sources.list).

---

