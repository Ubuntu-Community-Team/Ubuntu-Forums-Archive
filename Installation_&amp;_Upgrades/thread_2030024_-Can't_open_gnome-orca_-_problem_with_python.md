---
title: "-Can't open gnome-orca - problem with python"
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by BlueEgg on 2012-07-20
Hi!
After upgrading to ubuntu 12.04 I can't open gnome-orca.
When I want to open orca I get always this error message:


```
Traceback (most recent call last):
   File "<string>", line 1, in <module>
   File "/usr/lib/python2.7/dist-packages/orca/orca.py", line 396, in 
<module>
     _settingsManager = SettingsManager()
   File "/usr/lib/python2.7/dist-packages/orca/settings_manager.py", 
line 126, in __init__
     self.setProfile(self.profile)
   File "/usr/lib/python2.7/dist-packages/orca/settings_manager.py", 
line 344, in setProfile
     self._setSettingsRuntime(self.general)
   File "/usr/lib/python2.7/dist-packages/orca/settings_manager.py", 
line 358, in _setSettingsRuntime
     self._setPronunciationsRuntime()
   File "/usr/lib/python2.7/dist-packages/orca/settings_manager.py", 
line 365, in _setPronunciationsRuntime
     pronunciation_dict.setPronunciation(key, value)
   File "/usr/lib/python2.7/dist-packages/orca/pronunciation_dict.py", 
line 66, in setPronunciation
     key = word.decode("UTF-8").lower().encode("UTF-8")
   File "/usr/lib/python2.7/encodings/utf_8.py", line 16, in decode
     return codecs.utf_8_decode(input, errors, True)
UnicodeEncodeError: 'ascii' codec can't encode character u'\xe4' in 
position 1: ordinal not in range(128)
```


Can someone help me solving this problem?

Thank you very much

BlueEgg

---

