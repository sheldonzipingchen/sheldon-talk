---
title: "Neovim Markdown 配置"
date: 2022-07-01T14:36:58+08:00
description: 关于 Neovim 中的 Markdown 的一些实用的配置
draft: false
tags: [markdown, 笔记]
---

## 说明 #
之前的工作都是使用 VS Code 来完成，在时断时续的学习使用了 Vim 之后，慢慢发现自己的大部分的工作，都可以直接使用Vim 来完成了。于是逐渐开始完善 Vim 的配置。相对于 Macvim 来说，Neovim 会更容易使用一些，也就把自己的主力编辑器迁移到这上来了。

## 编辑Markdown #
在编辑 Markdown 文件的时候，有代码片段的支持可以很有效的提高我们编辑的效率。
这方面，我们可以用 [UltiSnips](https://github.com/SirVer/ultisnips) 
结合上 [vim-snippets](https://github.com/honza/vim-snippets) ，
就可以提供很多有用的代码片段。

我是使用 [vim-plug](https://github.com/junegunn/vim-plug) 进行安装：
```
Plug 'SirVer/ultisnips'
Plug 'honza/vim-snippets'
```

我们需要配置 UltiSnips 之后才能使用，下面是一个怎样配置的例子：
```
" 触发提示. 如果你使用的是 https://github.com/Valloric/YouCompleteMe ，请不要使用 tab 触发，改用其它的
let g:UltiSnipsExpandTrigger="<tab>"  " 使用 <Tab> 键触发提示
let g:UltiSnipsJumpForwardTrigger="<c-j>"
let g:UltiSnipsJumpBackwardTrigger="<c-k>"
```

如果使用了上面的配置，在我们输入了 `link` 然后再按下 `<Tab>` 以后，
会自动扩展成如下的文本：
```
[Text](https://www.url.com)
```

你需要把 `Text` 里的内容，替换成你实际需要显示的链接内容。
通过设置 `UltiSnipsJumpForwardTrigger` 和 `UltiSnipsJumpBackwardTrigger` 的值，
可以改变跳到下一个文本区或者是上一个文本区的快捷键。

以下是一些常用的代码片段：
- 标题:
    + 一级：`sec`
    + 二级：`ssec`
    + 三级：`sssec`
    + 四级：`par`
    + 五级：`spar`
- 链接：
    + 内联链接：`link`
    + 引用链接：`refl`
    + 图片链接：`img`
- 代码块：
    + 代码块：`cbl`
    + 内联代码块：`ilc`
- 文本样式：
    + 斜体：`*`
    + 粗体：`**`
    + 斜体加粗体：`***`
- 通用：
    + 日期：`date`
    + 时间：`time`
    + 日期时间：`datetime`
    + ISO 格式的日期：`diso`

## 无干扰写作
在我们写作的时候，有时需要关注于写作本身，临时关闭一些干扰的元素。
这个插件 [goyo](https://github.com/junegunn/goyo.vim) 可以帮助我们实现这个目标，
下面是通过 vim-plug 来安装这个插件：
```
Plug 'junegunn/goyo.vim'
```

在安装完毕以后，我们可以通过 `Goyo` 命令，来切换普通模式或者是无干扰模式。
Goyo 的作者同时也建议安装 [limelight](https://github.com/junegunn/limelight.vim)，
来高亮显示当前行。

首先，通过 vim-plug 来安装：
```
Plug 'junegunn/limelight.vim'
```

安装完成以后，我们可以通过 `Limelight` 来激活它；通过 `Limelight!` 来停用它。

我们也可以通过配置，在使用 goyo 的同时，激活 limelight：
```
autocmd! User GoyoEnter Limelight
autocmd! User GoyoLeave Limelight!
```


