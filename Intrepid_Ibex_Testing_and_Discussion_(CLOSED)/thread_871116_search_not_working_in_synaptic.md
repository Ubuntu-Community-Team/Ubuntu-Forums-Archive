---
title: "search not working in synaptic"
date: 2008-07-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phidia on 2008-07-26
In my x86_64 install of ibex search in synaptic is not functioning-can't enter anything into the search box. Has this been reported and/or is it something others here know about?

---

### Post by taavikko on 2008-07-26
Confirming this behaviour on 32bit installation.
If you meant the "quick search"

---

### Post by Elfy on 2008-07-26
> **taavikko said:**
> confirming this behaviour on 32bit installation.
If you meant the "quick search"

+1

---

### Post by cariboo on 2008-07-26
I posted a bug #244619 about this problem about two weeks ago.

Jim

---

### Post by phidia on 2008-07-26
Yeah I did mean quick search & thanks for letting me know it's been reported.

---

### Post by ronacc on 2008-07-26
you can get quick search working by installing apt-xapian-index , it seems to have been "left out" of the defaults .

---

### Post by Eclipse. on 2008-07-26
Yeap, apt-xapian-index is the problem, I had the same problem only firgured it out after some help from mvo on the mailing lists.

There is a bug filed on synaptic that it should depend on apt-xapian-index.

---

### Post by cariboo on 2008-07-27
Thanks guys I added apt-xapian-index as a dependency to the bug.

Jim

---

