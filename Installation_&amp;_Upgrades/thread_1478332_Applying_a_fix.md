---
title: "Applying a fix ?"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by papadilbert on 2010-05-09
I am experiencing a problem that would seem to be resolved by applying this fix. How do I apply it?


 Attached the patch included in 0.0.9+nmu2.

diff --git a/debian/changelog b/debian/changelog
index 8fb6ea6..f8fd3dc 100644
--- a/debian/changelog
+++ b/debian/changelog
@@ -4,6 +4,8 @@ sysconfig (0.0.9+nmu2) unstable; urgency=low
   * Allow for driver name change in sysfs for CTC network devices in  Linux
     kernel 2.6.33. Closes: #566632.
   * Correct variable use in hwup-ccw-group script. Closes: #566635.
+  * Also set buffer and protocol options both for the (old) ctc module  and
+    the (current) ctcm modules. Closes: #566629.
 
  -- Frans Pop <fjp@xxxxxxxxxx>  Thu, 29 Apr 2010 10:50:24 +0200
 
diff --git a/etc/sysconfig/scripts/hardware/hwup-ccw-group 
b/etc/sysconfig/scripts/hardware/hwup-ccw-group
index 491e7d6..59b3ec1 100755
--- a/etc/sysconfig/scripts/hardware/hwup-ccw-group
+++ b/etc/sysconfig/scripts/hardware/hwup-ccw-group
@@ -95,16 +95,19 @@ write_setting () {
   fi
 }

---

### Post by mörgæs on 2010-05-10
Patches appear automatically through the updates. If the patch comes from Debian ('upstream') like this one, it can take a little longer to get to the Ubuntu repositories.

Just add the updates and you will be fine.

---

