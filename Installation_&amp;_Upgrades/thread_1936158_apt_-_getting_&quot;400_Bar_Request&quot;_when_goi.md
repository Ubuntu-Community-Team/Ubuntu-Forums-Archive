---
title: "apt - getting &quot;400 Bar Request&quot; when going through an ISA server"
date: 2012-03-05
forum: Installation &amp; Upgrades
---

### Post by eantoranz on 2012-03-05
Hi!

I just finished installing (kubuntu) natty (cause that's the installer I have at hand) and I want to upgrade to oneiric however, when I try to update the package information I get "400 Bad Request". I'm going through an isa server and I think that might me the problem.

From what the output of apt is sending, it's asking for the grong file (by not appending the gz extension):


W: Imposible obtener [http://co.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages](http://co.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages)  400  Bad Request ( Datos no válidos.  )


I tried checking if I could download the file by going through the server, and it's possible:

```

antoranz@pingui:/etc/apt$ telnet x.x.x.x 8080
Trying x.x.x.x...
Connected to x.x.x.x.
Escape character is '^]'.
GET http://co.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages HTTP/1.0

HTTP/1.1 404 Not Found
Via: 1.1 PLATA
Connection: close
Proxy-Connection: close
Date: Mon, 05 Mar 2012 20:15:04 GMT
Content-Type: text/html; charset=iso-8859-1
Server: Apache/2.2.22

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>404 Not Found</title>
</head><body>
<h1>Not Found</h1>
<p>The requested URL /ubuntu/dists/natty-updates/multiverse/binary-i386/Packages was not found on this server.</p>
<hr>
<address>Apache/2.2.22 Server at co.archive.ubuntu.com Port 80</address>
</body></html>
Connection closed by foreign host.
antoranz@pingui:/etc/apt$ telnet x.x.x.x 8080
Trying x.x.x.x...
Connected to x.x.x.x.
Escape character is '^]'.
GET http://co.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages.gz HTTP/1.0

HTTP/1.1 200 OK
Via: 1.1 PLATA
Connection: close
Proxy-Connection: close
Content-Length: 6283
Date: Mon, 05 Mar 2012 20:15:16 GMT
Content-Type: application/x-gzip
ETag: "3d3a4c9-188b-4ba82022f1f00"
Server: Apache/2.2.22
Accept-Ranges: bytes
Last-Modified: Mon, 05 Mar 2012 17:10:52 GMT

binary data is here

```

What's going on?

---

