---
title: "301 Moved Permanently for us.archive.ubuntu.com"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by Anupama on 2008-10-09
Hello,

I have written a simple proxy for apt, that checks and maintains a table as to which package was downloaded from which repository.

Everything was working correctly, till recently, when i started getting a 301 Moved Permanently Error for "us.archive.ubuntu.com". I can still download from other sites like "archive.canonical.com", etc.

This means i need to enable redirection in my proxy code. However, I am not able to find the redirected site!!
Can anyone please let me know what is the redirected site for "us.archive.ubuntu.com"?

Regards,
Anupama

---

### Post by Anupama on 2008-10-09
prat.canonical.com
leningradskaya.canonical.com
lithium.canonical.com

All 3 seem to be redirected.
I get the HTTP header as follows:

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz">here</a>.</p>
<hr>
<address>Apache/2.0.55 (Ubuntu) Server at lithium.canonical.com Port 80</address>
</body></html>

But my request to archive.ubuntu.com goes to one of the above servers.

If anyone knows, please let me know of a server where I can connect for these pages.

Regards,
Anupama

---

### Post by cariboo on 2008-10-09
You may want to stop using the gutsy archives as it's end of life is October 19/2008. In other word after 09/19/2008 there will be no more support for Gutsy.

Jim

---

