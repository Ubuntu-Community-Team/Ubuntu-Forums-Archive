---
title: "Eclipse and Android Development Tools after upgrade to 11.10"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by zigac on 2011-10-26
I have a problem with Eclipse IDE after i have upgraded to 11.10. I am using Kubuntu. There is no Android DT in the Eclipse after the upgrade, before everything was working perfectly. Even if i want to install the Android DT again from [https://dl-ssl.google.com/android/eclipse/](https://dl-ssl.google.com/android/eclipse/) , i get this error:

>  Cannot complete the install because one or more required items could not be found.
  Software being installed: Android Development Tools 14.0.0.v201110171935-205994 (com.android.ide.eclipse.adt.feature.group 14.0.0.v201110171935-205994)
  Missing requirement: Android Development Tools 14.0.0.v201110171935-205994 (com.android.ide.eclipse.adt.feature.group 14.0.0.v201110171935-205994) requires 'org.eclipse.wst.sse.core 0.0.0' but it could not be found

Can anyone help? Do i have to re-install Eclipse IDE? Thank you for your help.

---

### Post by kimdung161 on 2011-10-26
Yes, I 've got this error, and I re-installed Eclipse but it don't fixed, 
Please help me!!! Thanks so much.

---

### Post by amulus on 2011-10-27
Hi,

Same/similar problem for me as well:
Cannot complete the install because one or more required items could not be found.
  Software being installed: Android Development Tools 14.0.0.v201110171935-205994 (com.android.ide.eclipse.adt.feature.group 14.0.0.v201110171935-205994)
  Missing requirement: Android Development Tools 14.0.0.v201110171935-205994 (com.android.ide.eclipse.adt.feature.group 14.0.0.v201110171935-205994) requires 'org.eclipse.wst.sse.core 0.0.0' but it could not be found

---

### Post by amulus on 2011-10-27
Hmm,

This seems to be some kind of auhorization problem. After running "sudo eclipse" the installation seems to proceed. I installed the Eclipse under 11.10 with Ubuntu Software Center and it install Eclipse in a location where normal users do not apparently have writing rights...

---

### Post by zigac on 2011-11-01
Yes it is an authorization problem. Run Eclipse as admin with "sudo" command and then install the Android DT. It will work normal also in non admin mode.:D

Thanks for help!

---

