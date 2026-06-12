---
title: "AWS-CLI fails with certificate error"
date: 2018-02-12
forum: Installation &amp; Upgrades
---

### Post by scahartner on 2018-02-12
Amazon CLI fails with SSL certificate error:

[FONT=courier new]aws s3 ls

[SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:777)
[/FONT]

I tried using different version of aws-cli and the certifi package for both python 2 and 3, however non of them work and all so far have produced the same error shown above.

awscli/artful,artful,now 1.11.139-1 all [installed]
python3-certifi/artful,artful,now 2017.4.17-2 all [installed,automatic]

I also trying installing via pip and pip3 

pip3 list
awscli (1.11.139)
certifi (2017.4.17)

Any pointers on how to get this working

---

### Post by Habitual on 2018-02-12
Please see "aws configure" section at [https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html)

---

