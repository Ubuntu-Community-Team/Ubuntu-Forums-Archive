---
title: "Re-building Unity .deb packages"
date: 2017-07-16
forum: Installation &amp; Upgrades
---

### Post by donROGALesko on 2017-07-16
I'm on Ubuntu 16.04 and was following this guide: [https://ineed.coffee/1068/os-x-like-multitouch-gestures-for-macbook-pro-running-ubuntu-12-10/](https://ineed.coffee/1068/os-x-like-multitouch-gestures-for-macbook-pro-running-ubuntu-12-10/)
When trying to build the package:
```
dpkg-buildpackage -us -uc -nc
```
I run into an error:
```
cd /tmp/unity/unity-7.4.0+16.04.20160906/obj-x86_64-linux-gnu/tests && export NUX_FALLBACK_TEXTURE=TRUE && /tmp/unity/unity-7.4.0+16.04.20160906/tests/dummy-xorg-test-runner.sh ./test-gtest --gtest_output=xml:./test-gtest.xml && /tmp/unity/unity-7.4.0+16.04.20160906/tests/dummy-xorg-test-runner.sh ./test-gtest-slow --gtest_output=xml:./test-gtest-slow.xml && ./test-gtest-xless --gtest_output=xml:./test-gtest-xless.xml && ./test-gestures/test-gestures --gtest_output=xml:./test-gestures.xml && dbus-test-runner --max-wait=300 --task ./test-gtest-service --task-name test-service --task=./test-gtest-dbus --task-name=test-gtest-dbus --wait-for=com.canonical.Unity.Test --parameter=--gtest_output=xml:./test-gtest-dbus.xml --parameter=--gtest_filter=-TestCategoriesChanging*
The X server was not able to run in time
tests/CMakeFiles/check-headless.dir/build.make:64: recipe for target 'tests/CMakeFiles/check-headless' failed
make[5]: *** [tests/CMakeFiles/check-headless] Error 1
make[5]: Leaving directory '/tmp/unity/unity-7.4.0+16.04.20160906/obj-x86_64-linux-gnu'
CMakeFiles/Makefile2:4997: recipe for target 'tests/CMakeFiles/check-headless.dir/all' failed
make[4]: *** [tests/CMakeFiles/check-headless.dir/all] Error 2
make[4]: Leaving directory '/tmp/unity/unity-7.4.0+16.04.20160906/obj-x86_64-linux-gnu'
CMakeFiles/Makefile2:5004: recipe for target 'tests/CMakeFiles/check-headless.dir/rule' failed
make[3]: *** [tests/CMakeFiles/check-headless.dir/rule] Error 2
make[3]: Leaving directory '/tmp/unity/unity-7.4.0+16.04.20160906/obj-x86_64-linux-gnu'
Makefile:1452: recipe for target 'check-headless' failed
make[2]: *** [check-headless] Error 2
make[2]: Leaving directory '/tmp/unity/unity-7.4.0+16.04.20160906/obj-x86_64-linux-gnu'
debian/rules:56: recipe for target 'override_dh_auto_test' failed
make[1]: *** [override_dh_auto_test] Error 2
make[1]: Leaving directory '/tmp/unity/unity-7.4.0+16.04.20160906'
debian/rules:60: recipe for target 'build' failed
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2

```
Can someone let me know how can I solve this?

---

