---
title: "smtp and smtps connection problems"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by genesimmons4201 on 2008-11-14
Trying to setup email server and experiencing some issues with postfix and smtp. I have Imap services running

try to telnet to either service and get
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.


my net stat is

tcp        0      0 *:ssmtp                 *:*                     LISTEN     
tcp        0      0 *:smtp                  *:*                     LISTEN     
tcp        1      0 example.com:smtp LONDON14-127965791:3592 CLOSE_WAIT 
tcp        0      0 localhost:smtp          localhost:43910         ESTABLISHED
tcp        1      0 example.com:smtp LONDON14-127965791:3591 CLOSE_WAIT 
tcp        0      0 example.com:smtp an-out-0708.google:3317 ESTABLISHED
tcp        0      0 example.com.thought:smtp ecmcmx1.tdbank.ca:23485 ESTABLISHED
tcp        0      0 localhost:43910         localhost:smtp          ESTABLISHED
unix  2      [ ACC ]     STREAM     LISTENING     519887   private/smtp
unix  2      [ ACC ]     STREAM     LISTENING     519943   private/bsmtp

where example.com is my actual domain name is there....editted for security
thanks I was in the middle of testing it and it appears to just hang..

---

