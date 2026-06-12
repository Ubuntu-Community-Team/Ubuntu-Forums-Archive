---
title: "SSL been broken since the 19th?"
date: 2008-09-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by vidar268 on 2008-09-29
I use thunderbird for my university's IMAP mail server which uses SSL authentication. Ever since Sept 19th, I am unable to retrieve email from that account. Thunderbird returns the error "Unable to connect to your IMAP server. You may have exceeded the maximum number of connections to this server. If so, use the Advanced IMAP Server Settings dialog to reduce the number of cached connections."

Originally, I thought it was just a problem on my university's end, but that appears not to be the case. The default value for cached connections is 5, I've tried 3, 1, 0, and 25. None of these fixes the issue. Checking with the university helpdesk, it looks like that's the error thunderbird gives when it tries to connect to the server when SSL isn't set up. It was working perfectly fine before the 19th, and I haven't changed any configuration since then.

Searching around google, it looks like it's a product of a broken SSL setup. Anyone have any advice?

---

### Post by vidar268 on 2008-09-30
Anyone?

---

### Post by vidar268 on 2008-10-02
Seriously. Anyone.

---

### Post by wgrant on 2008-10-02
I've been using SSL and TLS in Thunderbird on Intrepid for many months now.

---

### Post by vidar268 on 2008-10-02
Ok so why else wouldn't it be working? It's not like I changed anything between then and now.

---

### Post by ammikulka on 2008-10-02
maybe a change on your schools part?

---

### Post by Hobbsee on 2008-10-02
Also using SSL and thunderbird here.  No problems.

---

