---
title: "google gadget compile errors in intrepid"
date: 2008-07-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tlayton_at_work on 2008-07-07
Anybody compiling Google Gadgets for Linux? Sometime over the past two weeks, I started getting this error on compile. I get it for both the 0.9.3 and svn. Done everything from start over and to reconfigure.

All the errors seem to be from the LOG function in ggadget/listbox_element.cc. Unfortunately, I cannot find anything from the net regarding this at all.

Any help would be appreciated. Thx.

```

/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../ggadget -I.. -I.. -I../.. -D__STDC_CONSTANT_MACROS                 -DNDEBUG       -DGGL_MODULE_DIR=\"/usr/local/lib/google-gadgets/modules\"               -DGGL_INCLUDE_DIR=\"/usr/local/include/google-gadgets\"                 -DGGL_SYSDEPS_INCLUDE_DIR=\"/usr/local/lib/google-gadgets/include\"             -DGGL_LIBEXEC_DIR=\"/usr/local/lib/google-gadgets\"             -DGGL_RESOURCE_DIR=\"/usr/local/share/google-gadgets\" -DGGL_HOST_LINUX=1 -DHAVE_X11=1 -DMOZILLA_FIVE_HOME=\"/usr/lib/xulrunner-devel-1.9/lib\" -DHAVE_PTHREAD=1  -O2 -Wall -Wconversion -Werror  -MT libggadget-1.0_la-listbox_element.lo -MD -MP -MF .deps/libggadget-1.0_la-listbox_element.Tpo -c -o libggadget-1.0_la-listbox_element.lo `test -f 'listbox_element.cc' || echo '../../ggadget/'`listbox_element.cc                      
 g++ -DHAVE_CONFIG_H -I. -I../../ggadget -I.. -I.. -I../.. -D__STDC_CONSTANT_MACROS -DNDEBUG -DGGL_MODULE_DIR=\"/usr/local/lib/google-gadgets/modules\" -DGGL_INCLUDE_DIR=\"/usr/local/include/google-gadgets\" -DGGL_SYSDEPS_INCLUDE_DIR=\"/usr/local/lib/google-gadgets/include\" -DGGL_LIBEXEC_DIR=\"/usr/local/lib/google-gadgets\" -DGGL_RESOURCE_DIR=\"/usr/local/share/google-gadgets\" -DGGL_HOST_LINUX=1 -DHAVE_X11=1 -DMOZILLA_FIVE_HOME=\"/usr/lib/xulrunner-devel-1.9/lib\" -DHAVE_PTHREAD=1 -O2 -Wall -Wconversion -Werror -MT libggadget-1.0_la-listbox_element.lo -MD -MP -MF .deps/libggadget-1.0_la-listbox_element.Tpo -c ../../ggadget/listbox_element.cc  -fPIC -DPIC -o .libs/libggadget-1.0_la-listbox_element.o          
cc1plus: warnings being treated as errors                                       
../../ggadget/listbox_element.cc: In member function ‘void ggadget::ListBoxElement::Impl::SetPendingSelection()’:                                               
../../ggadget/listbox_element.cc:114: error: format not a string literal and no format arguments                                                                
../../ggadget/listbox_element.cc: In member function ‘bool ggadget::ListBoxElement::Impl::ClearSelection(ggadget::ItemElement*)’:                               
../../ggadget/listbox_element.cc:134: error: format not a string literal and no format arguments                                                                
../../ggadget/listbox_element.cc: In member function ‘void ggadget::ListBoxElement::SetItemOverColor(const ggadget::Variant&)’:                                 
../../ggadget/listbox_element.cc:337: error: format not a string literal and no format arguments                                                                
../../ggadget/listbox_element.cc: In member function ‘void ggadget::ListBoxElement::SetItemSelectedColor(const ggadget::Variant&)’:                             
../../ggadget/listbox_element.cc:366: error: format not a string literal and no format arguments                                                                
../../ggadget/listbox_element.cc: In member function ‘void ggadget::ListBoxElement::SetItemSeparatorColor(const ggadget::Variant&)’:                            
../../ggadget/listbox_element.cc:393: error: format not a string literal and no format arguments                                                                
../../ggadget/listbox_element.cc: In member function ‘void ggadget::ListBoxElement::SetItemSeparator(bool)’:                                                    
../../ggadget/listbox_element.cc:415: error: format not a string literal and no format arguments                                                                
../../ggadget/listbox_element.cc: In member function ‘int ggadget::ListBoxElement::GetSelectedIndex() const’:                                                   
../../ggadget/listbox_element.cc:440: error: format not a string literal and no format arguments                                                                
../../ggadget/listbox_element.cc: In member function ‘void ggadget::ListBoxElement::SetSelectedIndex(int)’:                                                     
../../ggadget/listbox_element.cc:463: error: format not a string literal and no format arguments                                                                
../../ggadget/listbox_element.cc: In member function ‘ggadget::ItemElement* ggadget::ListBoxElement::GetSelectedItem()’:                                        
../../ggadget/listbox_element.cc:478: error: format not a string literal and no format arguments                                                                
../../ggadget/listbox_element.cc: In member function ‘const ggadget::ItemElement* ggadget::ListBoxElement::GetSelectedItem() const’:                            
../../ggadget/listbox_element.cc:496: error: format not a string literal and no format arguments                                                                
../../ggadget/listbox_element.cc: In member function ‘void ggadget::ListBoxElement::SelectRange(ggadget::ItemElement*)’:                                        
../../ggadget/listbox_element.cc:575: error: format not a string literal and no format arguments                                                                
../../ggadget/listbox_element.cc: In member function ‘virtual void ggadget::ListBoxElement::Layout()’:                                                          
../../ggadget/listbox_element.cc:649: error: format not a string literal and noformat arguments
make[4]: *** [libggadget-1.0_la-listbox_element.lo] Error 1
make[4]: Leaving directory `/home/tlayton/google-gadgets/google-gadgets-for-linux-0.9.3/build/ggadget'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/tlayton/google-gadgets/google-gadgets-for-linux-0.9.3/build/ggadget'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tlayton/google-gadgets/google-gadgets-for-linux-0.9.3/build/ggadget'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tlayton/google-gadgets/google-gadgets-for-linux-0.9.3/build'
make: *** [all] Error 2


```

---

### Post by plun on 2008-07-07
Yup, and I must use the --disable-werror option for configure

Builds just fine after that

It was commented after the 0.9.2 release

> If you still encounter compilation issues, please try --disable-werror
configure option, it'll let build script tolerants harmless warnings.

Have fun!

James Su 


[http://groups.google.com/group/google-gadgets-for-linux-user/browse_thread/thread/712f2aae6213e63f/9ecaddd7c3e1ae77?lnk=gst&q=werror#9ecaddd7c3e1ae77](http://groups.google.com/group/google-gadgets-for-linux-user/browse_thread/thread/712f2aae6213e63f/9ecaddd7c3e1ae77?lnk=gst&q=werror#9ecaddd7c3e1ae77)

I have not filed any bug to Google about ths (running unstable software)

---

