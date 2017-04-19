<!--- @file
  HII Image Packs

  Copyright (c) 2017, Intel Corporation. All rights reserved.<BR>

  Redistribution and use in source (original document form) and 'compiled'
  forms (converted to PDF, epub, HTML and other formats) with or without
  modification, are permitted provided that the following conditions are met:

  1) Redistributions of source code (original document form) must retain the
     above copyright notice, this list of conditions and the following
     disclaimer as the first lines of this file unmodified.

  2) Redistributions in compiled form (transformed to other DTDs, converted to
     PDF, epub, HTML and other formats) must reproduce the above copyright
     notice, this list of conditions and the following disclaimer in the
     documentation and/or other materials provided with the distribution.

  THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR
  IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
  MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO
  EVENT SHALL TIANOCORE PROJECT  BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
  PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
  OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
  WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
  OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF
  ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

-->

# 2 HII Image Packs

EDK II Image Description files used for creating HII Image Packs have the
following format in EBNF:

```c
<ImageDefFileFormat> :: = <CommentLines>*
                          <Content>+
<CommentLines>       :: = "//" <AsciiString> <EOL>
<AsciiString>        :: = [ <TS>* <AsciiChars>* ]*
<AsciiChars>         ::= (0x21 - 0x7E)
<EOL>                ::= <TS> 0x0D 0x0A
<TabSpace>           ::= {<Tab>} {<Space>}
<TS>                 ::= <TabSpace>*
<MTS>                ::= <TabSpace>+
<Content>            ::= {<BlankLine>} {<ImageLine>}
<BlankLine>          ::= <EOL>
<ImageLine>          ::= <TS> "#image" <ImageID> [<TRANS>] <Filename> <EOL>
<ImageID>            ::= <MTS> (a-zA-Z)(a-zA-Z0-9_)*
<TRANS>              ::= <MTS> "TRANSPARENT"
<Filename>           :: =<MTS> <Word> ["." <Extension>]
<Word>               ::= (a-zA-Z0-9_)(a-zA-Z0-9_-,)*
<Extension>          ::= (a-zA-Z0-9_-)+
```

## 2.1 Definitions

**_Filename_**

Alphanumeric characters with optional period ".", dash "-" and/or underscore
"_" characters. A period character may not be followed by another period
character. No whitespace characters are permitted.

## 2.2 Example

```c
//  The Image definition file
//
// Copyright (c) 2017, Intel Corporation. All rights reserved.<BR>
// This program and the accompanying materials are licensed and made available under
// the terms and conditions of the BSD License that accompanies this distribution.
// The full text of the license may be found at
// http://opensource.org/licenses/bsd-license.php.
//
// THE PROGRAM IS DISTRIBUTED UNDER THE BSD LICENSE ON AN "AS IS" BASIS,
// WITHOUT WARRANTIES OR REPRESENTATIONS OF ANY KIND, EITHER EXPRESS OR IMPLIED.
//

#image IMG_LOGO       TRANSPARENT  Logo.bmp
#image IMG_FULL_LOGO               Logo.jpg
#image IMG_OEM_LOGO                Logo.png
```
