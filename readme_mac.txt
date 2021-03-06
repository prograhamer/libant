/*
This software is subject to the license described in the License.txt file 
included with this software distribution. You may not use this file except in compliance 
with this license.

Copyright (c) Dynastream Innovations Inc. 2013
All rights reserved.
*/

!!!!!!!!!!!!!!!!! PLEASE CHECK IMPORTANT NOTES AT THE BOTTOM !!!!!!!!!!!!!!!!!!!!

The library files and demo programs use generic C and C++ and should compile
with any standard C++ compiler. The source code in these directories can be compiled 
with GCC, and a project is provided for XCode, included with the Mac OS X Developer 
Tools

http://connect.apple.com/

Project Hierarchy ...


                    ANT_LIB
                       |
                       |
                       |
             --------------------
             |                  |
             |                  |
             |                  |
          ANT_DYLIB           DEMO_LIB
             |
             |
             |
         DEMO_DYLIB


---------------------------------------------------------------------------------


Description of targets ...

ANT_LIB

This is the main ANT library source code. It includes the low level serial
driver required to communicate with the USB stick as well as ANT message framing.

This target produces as output a static library, libantbase.a.

ANT_DYLIB

Based on the ANT library (ANT_LIB) this project defines a C dynamic library interface
for Mac OS X 10.3 and later, which may be imported into other languages that 
support dynamic libraries. Use of the ANT dynamic library interface greatly simplifies 
Mac OS X application development with ANT.
A binary release version of the ANT dynamic library, libant.dylib, is available in the 
BIN directory.

DEMO_LIB

A simple command line application built on top of the ANT library that demonstrates
how to setup ANT channels and data messages. 

DEMO_DYLIB

A simple command line application built on top of the ANT Dynamic Library that demonstrates how
to load the dynamic library (libant.dylib) and setup ANT channels and data messages.  

---------------------------------------------------------------------------------
** Important ** Using dynamic libraries

After compiling an application using the dynamic library, make sure that the binary version of the 
ANT dynamic library is either in the same path as the executable, or in a path specified by either 
of the following environment variables:
LD_LIBRARY_PATH
DYLD_LIBRARY_PATH
DYLD_FALLBACK_LIBRARY_PATH

The default value of DYLD_FALLBACK_LIBRARY_PATH (used when this variable is not set), 
is $HOME/lib;/usr/local/lib;/usr/lib.

---------------------------------------------------------------------------------
** Important ** Setting the network key.

Before the ANT Library will compile, the ANT-FS network key must be set. Inside 
the file ANT_LIB\software\ANTFS\antfs_host.cpp, set the key to the ANT-FS network
key or to all 0's.

---------------------------------------------------------------------------------
** Important ** A note about LOG files. 

Log files are not generated by the ANT library and dynamic library by default. To enable
logging, the library must be compiled with the DEBUG_FILE define and subsequently
enabled using the DSIDebug::Init and DSIDebug::SetDebug function. 
In the projects included, this option is disabled by default in the Release configuration,
and enabled in the Debug configuration.

---------------------------------------------------------------------------------
** Important ** A note about drivers

The ANT dynamic library uses the MacOS X I/O Kit device interface mechanism to directly interact 
with the USB hardware.
No drivers are needed to add support for the ANT USB1 or USB2 stick, however, the libraries
are backwards compatible with systems using the VCP drivers from Silicon Labs for USB1.











