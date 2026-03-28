  // 更新邀請數
  const count = (userInvites.get(inviter.id) || 0) + 1;
  userInvites.set(inviter.id, count);

  console.log(`${inviter.tag} 邀請了 ${member.user.tag}`);

  // 🎁 滿10人獎勵
  if (count === 10) {
    const channel = guild.systemChannel;
    if (channel) {
      channel.send(
        `🎉 恭喜 <@${inviter.id}> 邀請達 10 人！獲得皮膚箱 🎁`
      );
    }
  }

  invites.set(guild.id, newInvites);
});

client.login(process.env.TOKEN);
