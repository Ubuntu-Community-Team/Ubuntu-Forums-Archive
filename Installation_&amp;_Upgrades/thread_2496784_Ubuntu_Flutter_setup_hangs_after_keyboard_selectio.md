---
title: "Ubuntu Flutter setup hangs after keyboard selection"
date: 2024-04-12
forum: Installation &amp; Upgrades
---

### Post by uriegel on 2024-04-12
I want to install Ubuntu on my computer, but the flutter setup hangs after keyboard selection with the following error:

flutter: DEBUG subiquity_client: ==> setKeyboard(KeyboardSetting(layout: de, variant: , toggle: null)) null
flutter: ERROR ubuntu_bootstrap: Unhandled exception
    StackOverflowError: Stack Overflow
#0      _OperatorEqualsAndHashCode._hashCode (dart:collection-patch/compact_hash.dart)
#1      _LinkedHashSetMixin.add (dart:collection-patch/compact_hash.dart)
#2      _NativeFinalizer.attach (dart:ffi-patch/ffi_native_finalizer_patch.dart)
#3      UdevFinalizer.attach (package:udev/src/finalizer.dart)
#4      new UdevContext._ (package:udev/src/context.dart)
#5      UdevContext.fromPointer (package:udev/src/context.dart)
#6      new UdevContext (package:udev/src/context.dart)
#7      UdevDevice._createDevice.<anonymous closure> (package:udev/src/device.dart)
#8      using (package:ffi/src/arena.dart)
#9      UdevDevice._createDevice (package:udev/src/device.dart)
#10     UdevDevice.fromSyspath.<anonymous closure> (package:udev/src/device.dart)
#11     using (package:ffi/src/arena.dart)
#12     UdevDevice.fromSyspath (package:udev/src/device.dart)
#13     _UdevSyspathDeviceInfo._getDevice (package:ubuntu_provision/src/services/udev_service.dart)
#14     UdevDeviceInfo.modelName (package:ubuntu_provision/src/services/udev_service.dart)
#15     NetworkDevice._updateUdi (package:ubuntu_provision/src/network/network_device.dart)
#16     NetworkDevice._setDevice (package:ubuntu_provision/src/network/network_device.dart)
#17     NetworkDevice.updateDevice (package:ubuntu_provision/src/network/network_device.dart)
#18     NetworkDeviceModel.updateDevices (package:ubuntu_provision/src/network/network_device.dart)
#19     ChangeNotifier.notifyListeners (package:flutter/src/foundation/change_notifier.dart)
#20     SafeNotifierMixin.notifyListeners (package:safe_change_notifier/src/notifier_mixin.dart)
#21     NetworkDevice.updateDevice (package:ubuntu_provision/src/network/network_device.dart)
#22     NetworkDeviceModel.updateDevices (package:ubuntu_provision/src/network/network_device.dart)
#23     ChangeNotifier.notifyListeners (package:flutter/src/foundation/change_notifier.dart)
#24     SafeNotifierMixin.notifyListeners (package:safe_change_notifier/src/notifier_mixin.dart)
#25     NetworkDevice._updateUdi (package:ubuntu_provision/src/network/network_device.dart)

---

