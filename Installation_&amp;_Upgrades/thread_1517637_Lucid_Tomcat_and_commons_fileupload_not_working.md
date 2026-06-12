---
title: "Lucid Tomcat and commons fileupload not working"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by bobmanc on 2010-06-25
I am trying to build a server on AWS using the latest Lucid image from Canonical. I load java and tomcat and when I deploy my webapp it runs fine except for when I try to upload files using commons fileupload. Then I get the following error.

ERROR : Jun 16, 2010 14:53:16 [CommonsLogger.java:27] : Unable to parse request
org.apache.commons.fileupload.FileUploadException: Processing of multipart/form-data request failed. javax.servlet.context.tempdir/upload_2bd97087_129421bad1c__8000_00000000.tmp (No such file or directory)

the javax.servlet.context.tempdir points to /var/lib/tomcat6/work/Catalina/localhost/myapp which exists and to test I was able to create a new file there in my code.

This wan’t happening with the karmic build of tomcat. as far as I know everything else is the same. Any insight on this would be greatly appreciated.

---

### Post by bobmanc on 2010-06-29
SOLVED: Turns out the issue was with Struts2 feeding fileupload a bad directory. If tomcat was root it worked anyway. Not sure how it worked in Karmic.

---

