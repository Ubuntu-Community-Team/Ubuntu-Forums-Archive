---
title: "QtWebKit and QtSvg packages"
date: 2015-04-24
forum: Installation &amp; Upgrades
---

### Post by andrew218 on 2015-04-24
Hi guys,

I am trying to install Mendeley desktop in Ubuntu 12.04 but when I try call Mendeley from the terminal I get this message:

"To run Mendeley Desktop you may need to install the QtWebKit and QtSvg packages provided by your Linux distribution.
Using bundled SSL runtime libraries"

Now, what are these QtWebKit and QtSvg packages? How can I get them?

Thank you very much!

---

### Post by dino99 on 2015-04-24
there is no details about these dependencies  ;)  [http://linuxg.net/how-to-install-mendeley-desktop-1-9-2-on-ubuntu-13-04-12-10-12-04-linux-mint-15-14-13-elementary-os-0-2-and-pear-os-8/](http://linuxg.net/how-to-install-mendeley-desktop-1-9-2-on-ubuntu-13-04-12-10-12-04-linux-mint-15-14-13-elementary-os-0-2-and-pear-os-8/)

and you need to register for creating an account; not a real opensource spirit.

but 'pdftk' from ubuntu archive can do a lot too:

If PDF is electronic paper, then PDFtk is an electronic stapler-remover, hole-punch, binder, secret-decoder-ring, and X-Ray-glasses. PDFtk is a simple tool for doing everyday things with PDF documents. Keep one in the top drawer of your desktop and use it to:
 - Merge PDF documents
 - Split PDF pages into a new document
 - Decrypt input as necessary (password required)
 - Encrypt output as desired
 - Fill PDF Forms with FDF Data and/or Flatten Forms
 - Apply a Background Watermark
 - Report PDF on metrics, including metadata and bookmarks
 - Update PDF Metadata
 - Attach Files to PDF Pages or the PDF Document
 - Unpack PDF Attachments
 - Burst a PDF document into single pages
 - Uncompress and re-compress page streams
 - Repair corrupted PDF (where possible)

---

### Post by andrew218 on 2015-04-24
Thank you very much for the link!
After the first command this is the answer I get:

"ERRORE: impossibile verificare il certificato di [www.mendeley.com](www.mendeley.com), rilasciato da "/C=US/O=GeoTrust, Inc./CN=RapidSSL CA":
  Impossibile verificare localmente l'autorità dell'emittente.
Per connettersi a [www.mendeley.com](www.mendeley.com) in modo non sicuro, usare "--no-check-certificate"

and if I try the second command there is still that does not work. Here the answer:

dpkg: errore nell'elaborare mendeleydesktop-latest (--install):
 impossibile accedere all'archivio: File o directory non esistente
Si sono verificati degli errori nell'elaborazione:
 mendeleydesktop-latest

Please, what should I do?

Thank you

---

### Post by dino99 on 2015-04-24
'impossibile verificare il certificato' means you are installing a third party package (non ubuntu one); can ignore it.

'  File o directory non esistente' maybe you need to chmod +x  that app first
[http://community.linuxmint.com/tutorial/view/1525](http://community.linuxmint.com/tutorial/view/1525)

---

