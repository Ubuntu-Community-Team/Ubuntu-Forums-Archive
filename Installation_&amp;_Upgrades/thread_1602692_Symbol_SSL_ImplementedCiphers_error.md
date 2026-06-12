---
title: "Symbol SSL_ImplementedCiphers error"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by simonjester on 2010-10-21
The most recent update impacted my thunderbird-3.0.  When launched I get these error messages
/usr/lib/thunderbird-3.0.3pre/thunderbird-bin: Symbol `SSL_ImplementedCiphers' has different size in shared object, consider re-linking
/usr/lib/thunderbird-3.0.3pre/thunderbird-bin: symbol lookup error: /usr/lib/libnssutil3.so.1d: undefined symbol: PL_ClearArenaPool

I can only assume the libnssutil3 library was upgraded and this broke the library call in the thunderbird-3.0.  Any suggestions?  Install newer versions of thunderbird?

I'm running Linux 10.04 LTS.

---

### Post by nbo10 on 2010-10-22
I have the same problem. My system updated this morning, and now thunderbird will not open.

---

### Post by nbo10 on 2010-10-22
I downloaded the newest version of thunderbird and moved the files to /opt/thunderbird/. Then I use the command /opt/thunderbird/thunderbird to run the program. Everything works

---

### Post by simonjester on 2010-10-23
I did install another version of Thunderbird.  I have a new problem.  I need to import the mail local folders from my shredder version.  I can't figure out how to do that.  I need to scan the mozilla site I guess.

---

