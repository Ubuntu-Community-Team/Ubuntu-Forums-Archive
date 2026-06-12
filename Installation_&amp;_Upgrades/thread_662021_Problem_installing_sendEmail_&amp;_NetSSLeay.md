---
title: "Problem installing sendEmail &amp; Net::SSLeay"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by Metallinut on 2008-01-08
I'm trying to install sendEmail so I can send email to my gmail account (no MX in-house) from my command line.

I installed sendEmail via synaptic.  When I try to send an email using TLS, I get the error:
```
Jan 08 15:04:55 ubuntu2 sendEmail[2440]: ERROR => No TLS support!  SendEmail can't load required libraries. (try installing Net::SSLeay and IO::Socket::SSL)
```

So I downloaded the Net-SSLeay-1.32.tar.gz file...untarred it, and ran the following (with results)
```
jp@ubuntu2:~/installs/Net-SSLeay-1.32$ perl Makefile.PL
Cannot determine perl version info from lib/Net/SSLeay.pm
Cannot determine license info from lib/Net/SSLeay.pm
*** Found OpenSSL-0.9.8e installed in /usr
*** Be sure to use the same compiler and options to compile your OpenSSL, perl,
    and Net::SSLeay. Mixing and matching compilers is not supported.
Do you want to run external tests?
These tests *will* *fail* if you do not have network connectivity. [y]
*** Module::AutoInstall version 1.03
*** Checking for Perl dependencies...
[Core Features]
- Sub::Uplevel    ...loaded. (0.18)
- Test::Exception ...loaded. (0.26)
- Array::Compare  ...loaded. (1.14)
- Tree::DAG_Node  ...loaded. (1.06)
- Test::Warn      ...loaded. (0.10)
- MIME::Base64    ...loaded. (3.07)
*** Module::AutoInstall configuration finished.
Writing Makefile for Net::SSLeay
jp@ubuntu2:~/installs/Net-SSLeay-1.32$
```

Seems ok except for the perl version info and license info...

But then when I tried 
```
jp@ubuntu2:~/installs/Net-SSLeay-1.32$ sudo make install
```

It errors out... Here are the last few lines:
```
SSLeay.c:593: error: declaration for parameter âXS_Net__SSLeay_CTX_newâ but no such parameter
SSLeay.c:573: error: declaration for parameter âXS_Net__SSLeay_helloâ but no such parameter
SSLeay.c:555: error: declaration for parameter âXS_Net__SSLeay_constantâ but no such parameter
SSLeay.xs:352: error: declaration for parameter âssleay_ctx_cert_verify_cbsâ but no such parameter
SSLeay.xs:202: error: declaration for parameter âssleay_RSA_generate_key_cb_tâ but no such parameter
SSLeay.xs:201: error: declaration for parameter âssleay_ctx_cert_verify_cb_tâ but no such parameter
SSLeay.xs:200: error: declaration for parameter âssleay_ctx_passwd_cb_tâ but no such parameter
SSLeay.xs:194: error: declaration for parameter âssleay_ctx_passwd_cbsâ but no such parameter
SSLeay.xs:131: error: declaration for parameter âssleay_ctx_verify_callbacksâ but no such parameter
SSLeay.xs:127: error: declaration for parameter âperl_filehandle_tâ but no such parameter
SSLeay.c:6648: error: expected â{â at end of input
make: *** [SSLeay.o] Error 1
jp@ubuntu2:~/installs/Net-SSLeay-1.32$
```

I can post more, but the output overfills my terminal buffer...and I don't know how to output the on-screen results to an output file.

Any idea why the make install is failing?  Sorry...still kind of a newb.

---

### Post by Richardinho on 2008-02-09
I installed sendEmail by downloading the files from the website, extracting them to my desktop, then following the instructions in the readme file.

This basically involved checking where my perl binary was and making sure that it matched up with that given in the Shebang line.

Then copying the sendEmail file to a folder within the path-which happened to be /usr/local/sbin,
then setting the permissions of the file using chmod.

All this information is given in the readme file.

I on the other hand can't get it working as I don't know what my email address is supposed to be!
I have tried all the various email addresses in my thunderbird account without success.
I have tried completely made up email addressed.
Each time, the program tells me that the email has been successfully sent,but I don't receive anything!

I'm basically trying to set up a system so I can test PHP script on my local machine. I don't want to send out anything to the outside world.

Any help on that would be gratefully received.

---

