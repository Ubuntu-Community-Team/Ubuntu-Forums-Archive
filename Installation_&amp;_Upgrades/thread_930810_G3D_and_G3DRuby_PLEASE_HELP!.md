---
title: "G3D and G3DRuby? PLEASE HELP!"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by memories on 2008-09-26
I want a functional G3DRuby installation. I don't think I need G3D, but I can't install it either way. I am installing both from source. G3DRuby gives me the following:

> 
$ sh build.sh 
Host: x86_64-pc-linux-gnu
checking for main() in -lz... yes
checking for main() in -ljpeg... yes
checking for main() in -lGL... yes
checking for main() in -lGLU... yes
checking for main() in -lSDL... yes
checking for main() in -lG3D... yes
checking for main() in -lGLG3D... yes
creating Makefile
g++ -I. -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/include/ -I/usr/include/SDL  -fPIC -fno-strict-aliasing -g -g -O2  -fPIC   -c UserInput.cpp
UserInput.cpp: In function ‘VALUE UserInput_new(int, VALUE*, VALUE)’:
UserInput.cpp:36: error: no matching function for call to ‘G3D::UserInput::UserInput()’
/usr/include/GLG3D/UserInput.h:120: note: candidates are: G3D::UserInput::UserInput(G3D::GWindow*)
/usr/include/GLG3D/UserInput.h:34: note:                 G3D::UserInput::UserInput(const G3D::UserInput&)
UserInput.cpp: In function ‘VALUE UserInput_getMouseXY(int, VALUE*, VALUE)’:
UserInput.cpp:255: error: ‘class G3D::UserInput’ has no member named ‘getMouseXY’
UserInput.cpp: In function ‘VALUE UserInput_getMouseX(int, VALUE*, VALUE)’:
UserInput.cpp:272: error: ‘class G3D::UserInput’ has no member named ‘getMouseX’
UserInput.cpp: In function ‘VALUE UserInput_getMouseY(int, VALUE*, VALUE)’:
UserInput.cpp:288: error: ‘class G3D::UserInput’ has no member named ‘getMouseY’
UserInput.cpp: In function ‘VALUE UserInput_keyDown(int, VALUE*, VALUE)’:
UserInput.cpp:304: error: ‘KeyCode’ is not a member of ‘G3D::UserInput’
UserInput.cpp:304: error: expected `;' before ‘code’
UserInput.cpp:305: error: ‘code’ was not declared in this scope
UserInput.cpp: In function ‘VALUE UserInput_keyPressed(int, VALUE*, VALUE)’:
UserInput.cpp:321: error: ‘KeyCode’ is not a member of ‘G3D::UserInput’
UserInput.cpp:321: error: expected `;' before ‘code’
UserInput.cpp:322: error: ‘code’ was not declared in this scope
UserInput.cpp: In function ‘VALUE UserInput_keyReleased(int, VALUE*, VALUE)’:
UserInput.cpp:338: error: ‘KeyCode’ is not a member of ‘G3D::UserInput’
UserInput.cpp:338: error: expected `;' before ‘code’
UserInput.cpp:339: error: ‘code’ was not declared in this scope
UserInput.cpp: In function ‘VALUE UserInput_pressedKeys(int, VALUE*, VALUE)’:
UserInput.cpp:373: error: no matching function for call to ‘G3D::UserInput::pressedKeys(G3D::Array<short unsigned int>&)’
/usr/include/GLG3D/UserInput.h:210: note: candidates are: void G3D::UserInput::pressedKeys(G3D::Array<G3D::GKey>&) const
UserInput.cpp: In function ‘VALUE UserInput_releasedKeys(int, VALUE*, VALUE)’:
UserInput.cpp:392: error: no matching function for call to ‘G3D::UserInput::releasedKeys(G3D::Array<short unsigned int>&)’
/usr/include/GLG3D/UserInput.h:211: note: candidates are: void G3D::UserInput::releasedKeys(G3D::Array<G3D::GKey>&) const
UserInput.cpp: In function ‘VALUE UserInput_appHasFocus(int, VALUE*, VALUE)’:
UserInput.cpp:409: error: ‘class G3D::UserInput’ has no member named ‘appHasFocus’
UserInput.cpp: In function ‘VALUE UserInput_keyCodeToString(int, VALUE*, VALUE)’:
UserInput.cpp:506: error: ‘KeyCode’ is not a member of ‘G3D::UserInput’
UserInput.cpp:506: error: expected `;' before ‘i’
UserInput.cpp:507: error: ‘keyCodeToString’ is not a member of ‘G3D::UserInput’
UserInput.cpp:507: error: ‘i’ was not declared in this scope
UserInput.cpp: In function ‘VALUE UserInput_stringToKeyCode(int, VALUE*, VALUE)’:
UserInput.cpp:522: error: ‘stringToKeyCode’ is not a member of ‘G3D::UserInput’
make: *** [UserInput.o] Error 1


but I had to manually copy include/ and lib/ from G3D-7.00 to my /usr directory. I tried using the installer for G3D (./buildg3d) but it doesn't seem to work. It compiles and installs fine, but segfaults when I run testd. 

I just want to use G3D-Ruby. HELP!

---

